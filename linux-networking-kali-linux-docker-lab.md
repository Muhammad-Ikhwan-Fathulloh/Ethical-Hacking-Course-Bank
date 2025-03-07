# Hands-on: Praktikum Linux & Networking Fundamentals dengan Kali Linux di Docker

Berikut adalah panduan lengkap untuk praktikum Linux dan jaringan menggunakan Kali Linux yang dijalankan di Docker. Docker memungkinkan Anda menjalankan Kali Linux dalam container yang ringan dan portabel.

---

## 1. Persiapan Docker

### Langkah 1: Instal Docker
- Pastikan Docker sudah terinstal di sistem Anda. Jika belum, ikuti panduan instalasi resmi:
  - [Docker Installation Guide](https://docs.docker.com/get-docker/)

### Langkah 2: Verifikasi Instalasi Docker
- Jalankan perintah berikut untuk memastikan Docker berfungsi:
  ```bash
  docker --version
  docker run hello-world
  ```

---

## 2. Menjalankan Kali Linux di Docker

### Langkah 1: Pull Image Kali Linux
- Unduh image resmi Kali Linux dari Docker Hub:
  ```bash
  docker pull kalilinux/kali-rolling
  ```

### Langkah 2: Jalankan Container Kali Linux
- Jalankan container Kali Linux dengan akses terminal interaktif:
  ```bash
  docker run -it kalilinux/kali-rolling /bin/bash
  ```
  - Opsi `-it` memungkinkan Anda berinteraksi dengan terminal container.
  - `/bin/bash` menjalankan shell Bash di dalam container.

### Langkah 3: Update dan Install Tools
- Setelah masuk ke container, update sistem dan install tools yang diperlukan:
  ```bash
  apt update
  apt upgrade -y
  apt install -y nmap wireshark nano curl
  ```

---

## 3. Menggunakan Terminal Kali Linux di Docker

### Langkah 1: Perintah Dasar Linux
#### a. Menjelajahi Direktori
```bash
# Menampilkan direktori saat ini
pwd

# Menampilkan daftar file dan direktori
ls

# Pindah ke direktori home
cd ~
```

#### b. Membuat dan Mengelola File
```bash
# Buat direktori baru
mkdir hacking-lab

# Masuk ke direktori
cd hacking-lab

# Buat file baru
touch file.txt

# Edit file dengan nano
nano file.txt
  - Tekan `Ctrl + X` untuk keluar, `Y` untuk menyimpan.

# Menyalin file
cp file.txt file_backup.txt

# Menghapus file
rm file_backup.txt
```

#### c. Mengelola Izin File
```bash
# Lihat izin file
ls -l file.txt

# Ubah izin file
chmod 755 file.txt  # rwxr-xr-x
```

#### d. Mencari File dan Teks
```bash
# Cari teks dalam file
grep "keyword" file.txt
```

---

## 4. Analisis Lalu Lintas Jaringan dengan Wireshark di Docker

### Langkah 1: Jalankan Wireshark di Docker
- Wireshark memerlukan akses ke antarmuka jaringan host. Untuk menjalankan Wireshark di Docker, gunakan perintah berikut:
  ```bash
  docker run -it --net=host --cap-add=NET_ADMIN kalilinux/kali-rolling wireshark
  ```
  - Opsi `--net=host` memungkinkan container mengakses antarmuka jaringan host.
  - Opsi `--cap-add=NET_ADMIN` memberikan izin untuk menangkap paket.

### Langkah 2: Tangkap dan Analisis Paket
1. Buka Wireshark di dalam container.
2. Pilih antarmuka jaringan yang aktif (misalnya, `eth0`).
3. Mulai menangkap paket.
4. Gunakan filter untuk fokus pada protokol tertentu, misalnya:
   - `tcp.port == 80` untuk HTTP.
   - `ip.addr == 192.168.1.1` untuk alamat IP tertentu.

---

## 5. Scanning Jaringan dengan Nmap di Docker

### Langkah 1: Jalankan Nmap di Docker
- Untuk menjalankan Nmap di Docker, gunakan perintah berikut:
  ```bash
  docker run -it --net=host kalilinux/kali-rolling nmap
  ```

### Langkah 2: Contoh Scanning
- Lakukan scanning jaringan:
  ```bash
  # Scan alamat IP tertentu
  nmap 192.168.1.1

  # Scan seluruh subnet
  nmap 192.168.1.0/24

  # Deteksi sistem operasi
  nmap -O 192.168.1.1

  # Scan port tertentu
  nmap -p 80,443 192.168.1.1
  ```

---

## 6. Membuat Script Bash Sederhana di Docker

### Langkah 1: Buat File Script
- Buat file script di dalam container:
  ```bash
  nano myscript.sh
  ```

### Langkah 2: Isi Script
- Tambahkan kode berikut ke dalam file:
  ```bash
  #!/bin/bash
  echo "Hello, Docker!"
  ```

### Langkah 3: Berikan Izin Eksekusi
- Berikan izin eksekusi pada script:
  ```bash
  chmod +x myscript.sh
  ```

### Langkah 4: Jalankan Script
- Jalankan script:
  ```bash
  ./myscript.sh
  ```

---

## 7. Menyimpan Perubahan di Docker Container

### Langkah 1: Commit Container
- Jika Anda ingin menyimpan perubahan yang dibuat di container, commit container ke image baru:
  ```bash
  docker commit <container_id> my-kali-image
  ```

### Langkah 2: Jalankan Image Baru
- Jalankan container dari image yang telah di-commit:
  ```bash
  docker run -it my-kali-image /bin/bash
  ```

---

## 8. Tugas Praktikum

1. Buat direktori `hacking-lab` di dalam container Kali Linux dan buat 5 file teks di dalamnya.
2. Ubah izin salah satu file menjadi `rwxr--r--`.
3. Tangkap lalu lintas HTTP menggunakan Wireshark dan simpan hasilnya.
4. Lakukan scanning jaringan menggunakan Nmap pada subnet lokal.
5. Buat script Bash sederhana yang menampilkan informasi sistem (gunakan perintah `uname -a`).
