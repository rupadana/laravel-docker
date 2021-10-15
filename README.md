# Travellist - Laravel Demo App dengan Docker


## Build app
```
docker-compose build app
```

Ketika proses pembangunan selesai, Anda dapat menjalankan lingkungan dalam mode latar belakang dengan:

```
docker-compose up -d
```

Ini akan menjalankan kontainer Anda di latar belakang. Untuk menunjukkan informasi tentang kondisi layanan aktif, jalankan:

```
docker-compose ps
```

Lingkungan Anda kini sudah aktif dan berjalan, tetapi kita masih perlu mengeksekusi beberapa perintah untuk menyelesaikan pengaturan aplikasi. Anda dapat menggunakan perintah docker-compose exec untuk mengeksekusi perintah di dalam kontainer layanan, seperti ls -l untuk menampilkan informasi detail tentang berkas di dalam direktori aplikasi:
```
docker-compose exec app ls -l
```

Sekarang kita akan menjalankan composer install untuk menginstal dependensi aplikasi:

```
docker-compose exec app composer install
```

Hal terakhir yang perlu kita lakukan sebelum menguji aplikasi ini adalah menghasilkan kunci aplikasi unik dengan alat baris perintah Laravel artisan. Kunci ini digunakan untuk mengenkripsi sesi pengguna dan data sensitif lainnya:
```
docker-compose exec app php artisan key:generate
```

Sekarang, buka peramban Anda dan akses nama domain server atau alamat IP Anda pada porta 8000:

```
http://server_domain_or_IP:8000
```

Jika Anda ingin menghentikan sementara lingkungan Docker Compose sembari tetap mempertahankan kondisi semua layanan, jalankan:

```
docker-compose pause
```

Kemudian, Anda dapat melanjutkan layanan dengan:
```
docker-compose unpause
```

Untuk mematikan lingkungan Docker Compose dan menghapus semua kontainer, jaringan, dan volumenya, jalankan:

```
docker-compose down
```