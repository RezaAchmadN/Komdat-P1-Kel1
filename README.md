# ![](webapp/public/favicon-32x32.png) Planka
Planka adalah aplikasi yang menyediakan Kanban Board seperti Trello yang dibuat dengan React dan Redux

## Laporan Proyek Akhir KOM312 Komunikasi Data dan Jaringan

<img src="https://user-images.githubusercontent.com/48080398/111021533-a4388a00-83ff-11eb-9f1d-c54f6eb4ccc8.gif">

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

## Set Shared SSH & Firewall
Install openssh-server
```
sudo apt install openssh-serve
```
Lalu enable ssh nya dari sistem
```
sudo systemctl enable ssh
```
Jalankan shared ssh nya
```
sudo systemctl start ssh
```
aktifkan juga firewall nya untuk ssh
```
sudo ufw allow ssh
```
dan enable firewallnya
```
sudo ufw enable
```
# Instalasi
Pertama-tama, install Docker dan Docker Compose terlebih dahulu
## Instalasi Docker

<img src="https://user-images.githubusercontent.com/48080398/111018502-b90b2280-83eb-11eb-972a-97e2ee8a5671.png" width="200">

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
## Instalasi Docker Compose

<img src="https://user-images.githubusercontent.com/48080398/111018728-21a6cf00-83ed-11eb-956b-d90fe0c7985e.png" width="200">

>Pemasangan Docker Compose

Cek dan unduh bahwa docker-compose yang digunakan adalah versi ``1.27.4`` File yang diunduh akan disimpan pada directory ``/usr/local/bin/docker-compose``:
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
Pull data docker-compose dan mulai servis:
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
Setelah itu kita install menggunakan npm
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

![Planka Dashboard](https://user-images.githubusercontent.com/48080398/111018565-2c149900-83ec-11eb-8822-dab7c158680e.png)

# Pemakaian
Kita dapat membuat card dan juga melengkapi card tersebut dengan detail yang diinginkan. Seperti mengisi deskripsi, task, komentar dan juga berbagai macam fitur lainnya.

> Contoh tampilan Planka:

<img src=Documentation/file1.jpg height=400> 

# Pembahasan
Aplikasi ini sangat mirip dengan Trello, baik dari segi interface maupun penggunaan, karena seperti ide awalnya yaitu merupakan alternatif dari Trello itu sendiri. User dapat membuat board dengan card berisi task.

> Contoh tampilan Trello:

<img src=Documentation/file2.jpg height=400> 

**Perbedaan dengan Trello**
 - Perbedaan dengan Trello yang paling mendasar mungkin ada pada apa yang bisa diinput pada card oleh planka. Pada Planka, hanya bisa menambah members, label, due date, timer  dan attachment. Sedangkan untuk  Trello, dapat menginput checklist dan menambah cover juga.
 - Untuk fitur Actions yang terdapat ketika menambah detail Card, Planka hanya bisa Subscribe, Move, dan Delete. Sedangkan untuk Trello, dia bisa melakukan Copy, Make Template, Watch, Archive, dan Share
 - Tidak fitur Power Up
 - Tidak bisa membuat board menjadi Public atau Private

## Lisensi
Planka is [MIT licensed](https://github.com/plankanban/planka/blob/master/LICENSE).
