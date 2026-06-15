# Web Server

Web server merupakan komponen utama dalam layanan web yang berfungsi menerima permintaan (*request*) dari pengguna melalui browser dan mengirimkan kembali halaman atau data yang diminta. Komunikasi antara browser dan web server umumnya menggunakan protokol HTTP yang berjalan di atas protokol TCP.

## Langkah-Langkah

1. Buat sebuah folder dengan nama **week9**.

2. Buat file **serverweb.py** menggunakan Visual Studio Code.

3. Isi file **serverweb.py** dengan kode berikut:

```python
from socket import *
import sys

# membuat socket server (TCP)
serverSocket = socket(AF_INET, SOCK_STREAM)

# konfigurasi server
serverPort = 6789
serverSocket.bind(('', serverPort))
serverSocket.listen(1)

while True:
    # menerima koneksi dari client
    print('Ready to serve...')
    connectionSocket, addr = serverSocket.accept()

    try:
        # menerima request HTTP
        message = connectionSocket.recv(1024).decode()
        print(message)

        # mengambil nama file yang diminta
        filename = message.split()[1]

        # membuka file HTML
        f = open(filename[1:])
        outputdata = f.read()

        # mengirim header HTTP
        connectionSocket.send("HTTP/1.1 200 OK\r\n".encode())
        connectionSocket.send("Content-Type: text/html\r\n".encode())
        connectionSocket.send("\r\n".encode())

        # mengirim isi file
        for i in range(len(outputdata)):
            connectionSocket.send(outputdata[i].encode())

        connectionSocket.send("\r\n".encode())
        connectionSocket.close()

    except IOError:
        # mengirim pesan error jika file tidak ditemukan
        connectionSocket.send("HTTP/1.1 404 Not Found\r\n".encode())
        connectionSocket.send("Content-Type: text/html\r\n".encode())
        connectionSocket.send("\r\n".encode())
        connectionSocket.send(
            "<html><body><h1>404 Not Found</h1></body></html>".encode()
        )

        connectionSocket.close()

serverSocket.close()
sys.exit()
```

4. Buat file **index.html**.

5. Isi file **index.html** dengan kode berikut:

```html
<html>
<head>
    <title>Test Server</title>
</head>
<body>
    <h1>Hello World!</h1>
    <p>Ini merupakan halaman hasil dari program Web Server Python.</p>
</body>
</html>
```

## Hasil Percobaan

1. Buka terminal kemudian jalankan program server menggunakan perintah berikut:

```bash
py serverweb.py
```

2. Setelah server aktif, buka browser dan masukkan URL berikut:

```text
http://localhost:6789/HelloWorld.html
```

3. Jika file berhasil ditemukan oleh server, maka halaman web akan tampil seperti berikut.

![web](asset/image1.png)

4. Selanjutnya buka tab browser baru dan masukkan URL yang mengarah ke file yang tidak tersedia:

```text
http://localhost:6789/salah.html
```

5. Browser akan menampilkan halaman error seperti berikut.

![web](asset/image2(1).png)

### Analisis Hasil

- Server akan mengirimkan respons **404 Not Found** ketika file yang diminta tidak tersedia pada direktori server.
- Ketika file ditemukan, server mengirimkan respons **200 OK** beserta isi halaman HTML kepada browser.
- Hasil percobaan menunjukkan bahwa server mampu menangani permintaan yang berhasil maupun yang gagal dengan baik.

Program diawali dengan pembuatan socket TCP menggunakan modul `socket`. Setelah itu server dijalankan pada port 6789 dan berada dalam kondisi menunggu koneksi dari client. Saat browser mengirimkan request, server membaca nama file yang diminta. Jika file tersedia, server mengirimkan respons HTTP 200 OK beserta isi file HTML. Sebaliknya, jika file tidak ditemukan, server mengirimkan respons HTTP 404 Not Found. Implementasi ini masih menggunakan metode *single-threaded*, sehingga hanya dapat melayani satu koneksi client pada satu waktu.

---

# Latihan Web Tambahan

Pada latihan ini digunakan server yang sama seperti sebelumnya. Perubahan hanya dilakukan pada isi file **index.html** untuk menghasilkan tampilan yang berbeda.

## Langkah-Langkah

1. Buka file **index.html**.

2. Ubah isi file menjadi seperti berikut:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Server</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        h1 {
            font-size: 80px;
        }
    </style>
</head>

<body>
    <h1>Hello World</h1>
</body>
</html>
```

3. Jalankan kembali file **serverweb.py** melalui terminal.

4. Buka browser dan akses URL yang sama seperti sebelumnya agar halaman pada file **index.html** ditampilkan.

![web](asset/image3.png)

## Hasil Pengamatan

Setelah isi file HTML diubah, tampilan halaman web juga berubah sesuai dengan kode CSS yang ditambahkan. Tulisan **Hello World** ditampilkan dengan ukuran yang lebih besar dan berada tepat di tengah halaman. Hal ini menunjukkan bahwa web server berhasil mengirimkan file HTML terbaru kepada browser tanpa perlu melakukan perubahan pada program server.