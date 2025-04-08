# 🛡️ Pertemuan 4: Scanning & Enumeration

## 🌐 Tujuan Pembelajaran
Mahasiswa mampu mengidentifikasi layanan aktif dan kemungkinan kerentanannya pada suatu target menggunakan berbagai teknik scanning dan enumerasi.

---

## 📚 Materi Teori

### 1. Nmap untuk Scanning Jaringan
Nmap (Network Mapper) adalah tools open-source yang digunakan untuk:
- Menemukan host dalam jaringan
- Memetakan port terbuka
- Mendeteksi layanan dan versi
- Menemukan sistem operasi (OS Fingerprinting)

Contoh perintah:
```bash
nmap -sS -sV -O 192.168.1.1
```

### 2. Enumerasi dengan Netcat & Enum4linux
- **Netcat (nc)**: digunakan untuk menghubungkan ke port dan membaca banner:
```bash
nc 192.168.1.1 80
```
- **Enum4linux**: tool berbasis Linux untuk enumerasi informasi dari sistem berbasis Windows (SMB).
```bash
enum4linux -a 192.168.1.1
```

### 3. Banner Grabbing & Fingerprinting OS
- Banner grabbing adalah teknik untuk mendapatkan informasi layanan dan versi dari server
- OS Fingerprinting digunakan untuk menebak sistem operasi yang digunakan target

### 4. Web Scanning dengan Nikto & Dirb
- **Nikto**: scanner web server untuk mendeteksi celah umum dan file sensitif
```bash
nikto -h http://target.com
```
- **Dirb**: tool untuk brute-force direktori di website
```bash
dirb http://target.com
```

---

## 📝 Hands-on

### 1. Scanning Jaringan dengan Nmap
- Lakukan scanning pada alamat IP target (gunakan alamat dari lab lokal atau virtual environment seperti TryHackMe/VulnHub)
- Catat port yang terbuka, layanan yang berjalan, dan versi layanan

### 2. Enumerasi Layanan
- Gunakan Netcat untuk mencoba grab banner dari port terbuka (HTTP, SSH, FTP)
- Gunakan Enum4linux untuk target berbasis Windows

Contoh:
```bash
nc 10.10.10.10 80
```
```bash
enum4linux -a 10.10.10.10
```

---

## 📆 Referensi
- Gordon "Fyodor" Lyon - *Nmap Network Scanning*
- https://nmap.org/book/
- https://github.com/Tib3rius/enum4linux-ng
- https://tools.kali.org/information-gathering/nikto
- https://tools.kali.org/web-applications/dirb

---

## ⚠️ Etika Pengujian
Lakukan hanya pada sistem lab atau sistem milik pribadi. Jangan melakukan scanning dan enumerasi tanpa izin pada sistem publik atau milik orang lain.

