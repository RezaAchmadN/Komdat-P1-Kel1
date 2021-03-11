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
```
Update package terlebih dahulu
$ sudo apt update

Instal beberapa paket prasyarat yang memungkinkan apt menggunakan paket melalui HTTPS:
$ sudo apt install apt-transport-https ca-certificates curl software-properties-common

Kemudian tambahkan kunci GPG untuk repositori Docker resmi ke sistem:
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

Tambahkan repositori Docker ke sumber APT::
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"

Selanjutnya, perbarui package database dengan package Docker dari repo yang baru ditambahkan:
$ sudo apt update
```
Setelah itu pastikan bahwa kita menginstall dari repo Docker, bukan dari repo Ubuntu
```
apt-cache policy docker-ce
```
Setelah itu akan muncul output:
```
docker-ce:
  Installed: (none)
  Candidate: 5:19.03.9~3-0~ubuntu-focal
  Version table:
     5:19.03.9~3-0~ubuntu-focal 500
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



 
