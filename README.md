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

# Instalasi
Pertama-tama, install Docker dan Docker Compose terlebih dahulu
## Instalasi Docker
Update package terlebih dahulu
```
$ sudo apt update
```
Instal beberapa paket prasyarat yang memungkinkan apt menggunakan paket melalui HTTPS:
```
$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
Kemudian tambahkan kunci GPG untuk repositori Docker resmi ke sistem:
```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
Tambahkan repositori Docker ke sumber APT:
```
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```
Selanjutnya, perbarui package database dengan package Docker dari repo yang baru ditambahkan:
```
$ sudo apt update
```

Setelah itu pastikan bahwa kita menginstall dari repo Docker, bukan dari repo Ubuntu
```
@@ -51,7 +55,14 @@ docker-ce:
        500 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
```
Perhatikan bahwa **docker-ce** tidak diinstal, tetapi kandidat untuk penginstalan adalah dari repositori Docker untuk **Ubuntu 20.04 (focal)**

Setelah itu install docker
```
$ sudo apt install docker-ce
```
Untuk mengecek apakah sudah terinstall
```
docker --version
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

## Deployment
Clone repository dulu dari repo original
```
git clone https://github.com/plankanban/planka.git
```
Lalu pindah ke direktori planka
```
cd planka
```
Setelah itu kita install npm untuk node package management
```
npm install
```
Setelah itu bisa menggunakan database lokal atau menggunakan database yang sudah disediakan
```
docker-compose -f docker-compose-dev.yml up
```
Mulai server deployment:
```
npm start
```
