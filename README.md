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

Download docker-compose.yml
```
$ curl -L https://raw.githubusercontent.com/plankanban/planka/master/docker-compose.yml -o docker-compose.yml
```
Pull data composer dan mulai servis
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
