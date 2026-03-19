# MODUL 3
## Modul 3.2 Basic HTTP GET/response interaction 
Pada minggu ke-3 masih melanjutkan pembahasan pada modul 3 mengenai HTTP, namun pada bagian ini lebih difokuskan pada Basic HTTP GET/response interaction.

## Langkah-langkah percobaan
1. Pertama, buka aplikasi Wireshark.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_LOBBY.png)

2. Setelah Wireshark terbuka, pilih jaringan WiFi untuk memulai proses capture packet.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_WI-FI.png)

3. Pastikan proses capture sudah berjalan, kemudian buka browser dan akses link berikut: http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.html
![tampilan](..\Praktikun-Jarkom\assets\image\WS_JADIW.png)

4. Gunakan fitur filter seperti pada percobaan sebelumnya, yaitu dengan memasukkan filter HTTP untuk menampilkan paket yang diinginkan.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_HTTP.png)

5.Setelah selesai, hentikan proses capture. Kemudian pilih salah satu paket untuk melihat detail informasi yang ditampilkan.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_JADIL.png)

## Uji coba Web not found
Pada percobaan ini dilakukan pengujian dengan menggunakan alamat web yang tidak valid untuk melihat respon HTTP yang dihasilkan.

## Langkah-langkah percobaan
1. Jalankan aplikasi Wireshark, pilih jaringan WiFi, lalu mulai proses capture packet.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_WI-FI.png)

2. Terapkan filter HTTP untuk mempermudah pencarian paket.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_HTTP.png)

3. Selanjutnya, buka browser dan masukkan link HTTP yang telah dimodifikasi dengan tambahan karakter acak, misalnya:
http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.htmlregergev
![tampilan](..\Praktikun-Jarkom\assets\image\WS_404W.png)

4. Setelah itu, kembali ke Wireshark. Pada bagian HTTP akan terlihat status 404 (error) yang menandakan halaman tidak ditemukan.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_404L.png)


# Modul 3.3 Retrieving Long Documents 
Pada modul ini membahas tentang proses Retrieving Long Documents, yaitu pengambilan data berukuran besar seperti file atau halaman web panjang melalui hasil capture paket jaringan menggunakan protokol seperti HTTP, TCP, atau FTP.

## Langkah-langkah percobaan 
1. Buka Wireshark, pilih jaringan WiFi, lalu mulai capture packet.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_WI-FI.png)

2. Buka browser dan akses link berikut:
http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file3.html
![tampilan](..\Praktikun-Jarkom\assets\image\WS_ldJADIW.png)

3. Gunakan filter HTTP pada Wireshark untuk menampilkan paket yang berkaitan.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_HTTP.png)

4. Hentikan proses capture, kemudian pilih salah satu paket untuk melihat detail isi paket tersebut.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_ldJADIL.png)


# Modul 3.4 HTML Documents dengan Embedded Objects
Pada modul ini dipelajari tentang HTML yang memiliki objek tambahan di dalamnya, seperti gambar, CSS, atau JavaScript. Ketika halaman tersebut dibuka, browser akan mengirim beberapa request HTTP yang dapat diamati melalui Wireshark.

## Langkah-langkah percobaan
1. Jalankan Wireshark, pilih jaringan WiFi, dan mulai capture packet.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_WI-FI.png)

2. Buka browser dan akses link berikut:
http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file4.html
![tampilan](..\Praktikun-Jarkom\assets\image\WS_picJADIW.png)

3. Kembali ke Wireshark dan gunakan filter HTTP untuk melihat paket yang tertangkap.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_HTTP.png)

4. Setelah halaman terbuka, pada Wireshark akan muncul informasi seperti JPEG, yang menandakan adanya objek gambar yang ikut dimuat dalam halaman tersebut.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_picJADIL.png)


# Modul 3.5 HTTP Authentication
Pada modul ini dibahas mengenai HTTP Authentication, yaitu proses autentikasi saat pengguna mengakses halaman yang memerlukan username dan password, di mana proses tersebut dapat dilihat melalui paket HTTP di Wireshark.

## Langkah-langkah percobaan
1. Buka Wireshark, pilih jaringan WiFi, lalu mulai capture packet.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_WI-FI.png)

2. Buka browser dan akses link berikut:
http://gaia.cs.umass.edu/wireshark-labs/protected_pages/HTTP-wireshark-file5.html
![tampilan](..\Praktikun-Jarkom\assets\image\WS_loginUIW.png)
Akan muncul permintaan untuk memasukkan username dan password.

3. Masukkan username: wireshark-students dan password: network, lalu tekan enter.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_loginJADIW.png)

4. Setelah berhasil login, pada Wireshark akan terlihat paket dengan status Unauthorized sebagai bagian dari proses autentikasi tersebut.
![tampilan](..\Praktikun-Jarkom\assets\image\WS_loginJADIL.png)