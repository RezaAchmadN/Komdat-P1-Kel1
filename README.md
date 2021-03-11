# ![](webapp/public/favicon-32x32.png) Planka

## Laporan Proyek Akhir KOM312 Komunikasi Data dan Jaringan

## Step Pembuatan
- [Setup VM](#Setup-VM)
- [Instalasi](#Instalasi)
- [Demo](#Demo)

# Setup VM
Kami menggunakan VM untuk pemimplementasian instalasi Webapss Planka. Untuk menggunakan VM pada Windows ada beberapa langkah yang harus dilakukan. 
1. Download VM pada link berikut https://www.virtualbox.org/wiki/Downloads
2. Selesaikan proses instalasi pada VM yang anda punya. 
3. Download VDI pada link berikut https://ubuntu.com/download/desktop
4. Buat VM baru pada VM yang anda punya 
5. Tentukan name, machine folder,type dan version. Untuk type pilih Linux dan untuk version pilih Ubuntu (64-bit)
6. Tentukan Memory Size yang akan di alokasikan pada VM 
7. Buat Virtual Hard Disk baru dan pilih VDI 
8. Pilih Fixed Size pada type storage
9. Tentukan File location dan Size 
10. Setelah itu VM anda akan terbuat dan anda bisa start VM anda
11. Masukkan VDI yang anda punya pada start-up disk
12. Lakukan setup Ubuntu dan VM akan bisa anda pakai

#Instalasi
Pertama-tama, install Docker dan Docker Compose terlebih dahulu
## Instalasi Docker
```
$ cd ~
$ curl -sL https://deb.nodesource.com/setup_10.x -o nodesource_setup.sh
$ sudo bash nodesource_setup.sh
$ sudo apt install nodejs
```

## Instalasi Docker Composer
>Pemasangan Docker Compose

Cek dan unduh bahwa composer yang digunakan adalah versi ``1.27.4`` File yang diunduh akan disimpan pada directory ``/usr/local/bin/docker-compose``:
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
Pasang izin yang benar sehingga perintah docker-compose dapat dieksekusi: 
```
sudo chmod +x /usr/local/bin/docker-compose
```
Untuk memverifikasi bahwa penginstalan berhasil, jalankan:
```
docker-compose --version
```
Dan akan muncul keluaran seperti berikut:
```
Output
docker-compose version 1.27.4, build 40524192
```
###
> Pembuatan yml docker compose

Unduh docker-compose.yml:
```
$ curl -L https://raw.githubusercontent.com/plankanban/planka/master/docker-compose.yml -o docker-compose.yml
```
Pull data composer dan mulai servis:
```
$ sudo docker-compose up -d
```
