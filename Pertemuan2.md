# Pertemuan 2: Linux & Networking Fundamentals untuk Hacking

## Tujuan
Menguasai dasar-dasar sistem operasi dan jaringan untuk penetration testing.

---

## Materi Teori

### 1. Dasar-dasar Linux Command Line (CLI)
Linux Command Line Interface (CLI) adalah antarmuka berbasis teks untuk berinteraksi dengan sistem operasi Linux. CLI memungkinkan pengguna untuk menjalankan perintah, mengelola file, dan mengontrol sistem secara efisien.

#### Beberapa perintah dasar Linux:
- **`ls`**: Menampilkan daftar file dan direktori.
- **`cd`**: Mengubah direktori.
- **`pwd`**: Menampilkan direktori saat ini.
- **`mkdir`**: Membuat direktori baru.
- **`rm`**: Menghapus file atau direktori.
- **`cp`**: Menyalin file atau direktori.
- **`mv`**: Memindahkan atau mengganti nama file/direktori.
- **`nano`**: Editor teks sederhana di terminal.
- **`chmod`**: Mengubah izin file/direktori.
- **`sudo`**: Menjalankan perintah dengan hak akses superuser (root).
- **`grep`**: Mencari teks dalam file atau output.

---

### 2. Struktur File Linux & User Privileges
#### Struktur File Linux
- **`/`**: Direktori root, induk dari semua direktori.
- **`/home`**: Direktori home untuk pengguna.
- **`/etc`**: Berisi file konfigurasi sistem.
- **`/var`**: Berisi file yang sering berubah seperti log.
- **`/bin` dan `/usr/bin`**: Berisi perintah-perintah dasar.
- **`/root`**: Direktori home untuk root.

#### User Privileges
- **User**: Pengguna biasa dengan akses terbatas.
- **Root**: Superuser dengan akses penuh ke sistem.
- **Permissions**: Izin file/direktori (read `r`, write `w`, execute `x`).
  - Contoh: `rwxr-xr--` berarti:
    - Pemilik: baca, tulis, eksekusi (`rwx`).
    - Grup: baca, eksekusi (`r-x`).
    - Lainnya: hanya baca (`r--`).

---

### 3. TCP/IP, Ports, Protocols, dan Model OSI
#### TCP/IP
- Protokol komunikasi yang digunakan di internet.
- Terdiri dari 4 lapisan:
  1. **Application Layer** (HTTP, FTP, DNS).
  2. **Transport Layer** (TCP, UDP).
  3. **Internet Layer** (IP, ICMP).
  4. **Network Access Layer** (Ethernet, Wi-Fi).

#### Ports
- Titik akhir komunikasi dalam jaringan.
- Contoh:
  - **Port 80**: HTTP.
  - **Port 443**: HTTPS.
  - **Port 22**: SSH.

#### Protocols
- **HTTP/HTTPS**: Protokol web.
- **FTP**: Transfer file.
- **SSH**: Remote login aman.
- **DNS**: Resolusi nama domain.

#### Model OSI
- Model referensi 7 lapisan:
  1. **Physical Layer**.
  2. **Data Link Layer**.
  3. **Network Layer**.
  4. **Transport Layer**.
  5. **Session Layer**.
  6. **Presentation Layer**.
  7. **Application Layer**.

---

### 4. Wireshark untuk Sniffing Traffic
- **Wireshark**: Alat analisis jaringan untuk menangkap dan menganalisis paket data.
- Fitur:
  - Menangkap paket secara real-time.
  - Filter paket berdasarkan protokol, alamat IP, port, dll.
  - Analisis lalu lintas jaringan untuk keamanan.

---

### 5. Virtualization & Lab Setup dengan VMware/VirtualBox
- **Virtualisasi**: Membuat lingkungan virtual untuk menjalankan sistem operasi di dalam sistem operasi utama.
- **VMware/VirtualBox**: Perangkat lunak untuk membuat dan mengelola mesin virtual.
- **Lab Setup**:
  - Instal VMware/VirtualBox.
  - Buat mesin virtual dengan sistem operasi Linux (misalnya, Kali Linux).
  - Konfigurasi jaringan virtual untuk simulasi penetration testing.

---

## Hands-on

### 1. Menggunakan Terminal Linux
#### Contoh Perintah:
```bash
# Menampilkan daftar file
ls

# Pindah ke direktori
cd /home/user

# Buat file baru dengan nano
nano file.txt

# Ubah izin file
chmod 755 file.txt

# Cari teks dalam file
grep "keyword" file.txt

# Jalankan perintah sebagai root
sudo apt update
```

---

### 2. Analisis Lalu Lintas Jaringan dengan Wireshark
#### Langkah-langkah:
1. Buka Wireshark.
2. Pilih antarmuka jaringan yang aktif.
3. Mulai menangkap paket.
4. Gunakan filter untuk fokus pada protokol tertentu, misalnya:
   - `tcp.port == 80` untuk HTTP.
   - `ip.addr == 192.168.1.1` untuk alamat IP tertentu.
5. Analisis paket untuk memahami pola lalu lintas.

# Hands-on: Praktikum Linux & Networking Fundamentals

Berikut adalah panduan lengkap untuk praktikum Linux dan jaringan yang mencakup penggunaan terminal Linux, analisis lalu lintas jaringan dengan Wireshark, dan setup lab virtualisasi.

---

## 1. Menggunakan Terminal Linux

### Langkah 1: Membuka Terminal
- Di Linux, buka terminal dengan menekan `Ctrl + Alt + T` atau cari "Terminal" di menu aplikasi.

### Langkah 2: Perintah Dasar Linux
#### a. Menjelajahi Direktori
```bash
# Menampilkan direktori saat ini
pwd

# Menampilkan daftar file dan direktori
ls

# Menampilkan daftar file dengan detail (izin, ukuran, dll.)
ls -l

# Pindah ke direktori home
cd ~

# Pindah ke direktori tertentu
cd /var/log

# Kembali ke direktori sebelumnya
cd ..
```

#### b. Membuat dan Mengelola File
```bash
# Buat direktori baru
mkdir myfolder

# Masuk ke direktori
cd myfolder

# Buat file baru
touch file.txt

# Update Package List
apt update

# Add Nano
apt install nano

# View Version nano
nano --version

# Edit file dengan nano
nano file.txt
  - Tekan `Ctrl + X` untuk keluar, `Y` untuk menyimpan.

# Menyalin file
cp file.txt file_backup.txt

# Memindahkan file
mv file.txt ../file.txt

# Menghapus file
rm file_backup.txt

# Menghapus direktori
rm -r myfolder
```

#### c. Mengelola Izin File

| Mode        | Deskripsi                                                                                     | Contoh                   | Izin                                            |
|:------------|:----------------------------------------------------------------------------------------------|:-------------------------|:------------------------------------------------|
| `chmod 777` | Memberikan akses penuh (baca, tulis, jalankan) kepada semua orang                             | `chmod 777 file.txt`     | Pemilik: rwx <br> Grup: rwx <br> Lain-lain: rwx |
| `chmod 755` | Memberikan akses penuh kepada pemilik, dan akses baca dan jalankan kepada grup dan lain-lain  | `chmod 755 script.sh`    | Pemilik: rwx <br> Grup: r-x <br> Lain-lain: r-x |
| `chmod 644` | Memberikan akses baca dan tulis kepada pemilik, dan akses baca saja kepada grup dan lain-lain | `chmod 644 document.pdf` | Pemilik: rw- <br> Grup: r-- <br> Lain-lain: r-- |
| `chmod 600` | Memberikan akses baca dan tulis hanya kepada pemilik                                          | `chmod 600 private.key`  | Pemilik: rw- <br> Grup: --- <br> Lain-lain: --- |
| `chmod +x`  | Menambahkan izin jalankan ke file                                                             | `chmod +x script.sh`     | Menambahkan izin jalankan untuk semua           |
| `chmod -w`  | Menghapus izin tulis dari file                                                                | `chmod -w file.txt`      | Menghapus izin tulis untuk semua                |

```bash
# Lihat izin file
ls -l file.txt

# Ubah izin file
chmod 755 file.txt  # rwxr-xr-x
chmod +x file.txt  # Tambahkan izin eksekusi
chmod 644 file.txt # rw-r--r--

# Ubah kepemilikan file
sudo chown user:group file.txt
```

#### d. Mencari File dan Teks
```bash
# Cari file berdasarkan nama
find / -name "file.txt"

# Cari teks dalam file
grep "keyword" file.txt

# Cari teks dalam direktori secara rekursif
grep -r "keyword" /path/to/directory
```

#### e. Menggunakan `sudo`
```bash
# Install Sudo
apt update
apt install sudo

# Update daftar paket
sudo apt update

# Install aplikasi
sudo apt install nmap

# Jalankan perintah sebagai root
sudo su
```

---

## 2. Analisis Lalu Lintas Jaringan dengan Wireshark

### Langkah 1: Instal Wireshark
- Di Linux, instal Wireshark dengan perintah:
  ```bash
  sudo apt update
  sudo apt install wireshark
  ```

### Langkah 2: Menjalankan Wireshark
1. Buka Wireshark dari terminal atau menu aplikasi.
2. Pilih antarmuka jaringan yang aktif (misalnya, `eth0` atau `wlan0`).
3. Klik "Start" untuk mulai menangkap paket.

### Langkah 3: Filter Paket
- Gunakan filter untuk fokus pada jenis lalu lintas tertentu:
  - **HTTP**: `tcp.port == 80`
  - **HTTPS**: `tcp.port == 443`
  - **DNS**: `udp.port == 53`
  - **Alamat IP tertentu**: `ip.addr == 192.168.1.1`

### Langkah 4: Analisis Paket
1. Cari paket HTTP dengan filter `http`.
2. Klik paket untuk melihat detailnya:
   - **Frame**: Informasi umum tentang paket.
   - **Ethernet**: Alamat MAC sumber dan tujuan.
   - **IP**: Alamat IP sumber dan tujuan.
   - **TCP/UDP**: Port sumber dan tujuan.
   - **Data**: Isi paket (jika ada).

### Langkah 5: Simpan Hasil Capture
- Klik `File > Save As` untuk menyimpan hasil capture dalam format `.pcap`.

---

## 3. Virtualisasi & Lab Setup dengan VMware/VirtualBox

### Langkah 1: Instal VMware/VirtualBox
- Download dan instal VMware Workstation atau VirtualBox dari situs resmi:
  - VMware: [https://www.vmware.com](https://www.vmware.com)
  - VirtualBox: [https://www.virtualbox.org](https://www.virtualbox.org)

### Langkah 2: Download ISO Linux
- Download ISO sistem operasi Linux (misalnya, Kali Linux) dari situs resmi:
  - Kali Linux: [https://www.kali.org](https://www.kali.org)

### Langkah 3: Buat Mesin Virtual
1. Buka VMware/VirtualBox.
2. Klik "New" untuk membuat mesin virtual baru.
3. Beri nama mesin virtual (misalnya, "Kali Linux").
4. Pilih tipe sistem operasi (Linux) dan versi (Debian 64-bit).
5. Alokasikan RAM (minimal 2 GB) dan ruang disk (minimal 20 GB).
6. Pilih file ISO yang telah diunduh sebagai media instalasi.

### Langkah 4: Instal Sistem Operasi
1. Jalankan mesin virtual.
2. Ikuti langkah-langkah instalasi Kali Linux:
   - Pilih bahasa, lokasi, dan keyboard.
   - Konfigurasi partisi disk (gunakan opsi default).
   - Buat pengguna dan password.
3. Selesaikan instalasi dan reboot mesin virtual.

### Langkah 5: Konfigurasi Jaringan Virtual
1. Di VMware/VirtualBox, buka pengaturan mesin virtual.
2. Pilih "Network" dan atur adapter jaringan ke mode "Bridged" atau "NAT".
3. Jalankan mesin virtual dan periksa koneksi jaringan:
   ```bash
   ping google.com
   ```

---

## 4. Praktikum Lanjutan

### a. Scanning Jaringan dengan Nmap
- Install Nmap:
  ```bash
  sudo apt install nmap
  ```
- Lakukan scanning:
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

### b. Membuat Script Bash Sederhana
- Buat file script:
  ```bash
  nano myscript.sh
  ```
- Isi script:
  ```bash
  #!/bin/bash
  echo "Hello, World!"
  ```
- Berikan izin eksekusi:
  ```bash
  chmod +x myscript.sh
  ```
- Jalankan script:
  ```bash
  ./myscript.sh
  ```
