# 🛡️ Latihan: Web Application Hacking (OWASP Top 10)

## 📚 1. Pengenalan OWASP Top 10
OWASP (Open Web Application Security Project) adalah organisasi nirlaba yang fokus pada peningkatan keamanan perangkat lunak. Salah satu kontribusinya yang paling dikenal adalah daftar **OWASP Top 10**, yaitu sepuluh besar kerentanan keamanan aplikasi web yang paling umum dan berbahaya.

### OWASP Top 10 - 2021
| No | Kategori                                          | Kode |
|----|---------------------------------------------------|------|
| 1  | Broken Access Control                            | A01  |
| 2  | Cryptographic Failures                           | A02  |
| 3  | Injection                                        | A03  |
| 4  | Insecure Design                                  | A04  |
| 5  | Security Misconfiguration                        | A05  |
| 6  | Vulnerable and Outdated Components               | A06  |
| 7  | Identification and Authentication Failures       | A07  |
| 8  | Software and Data Integrity Failures             | A08  |
| 9  | Security Logging and Monitoring Failures         | A09  |
| 10 | Server-Side Request Forgery (SSRF)               | A10  |

## 🧠 2. Teori dan Praktik Eksploitasi Web (Studi Kasus: https://hackable-pentest.vercel.app)

### A01 - Broken Access Control
**Deskripsi:** Pengguna dapat mengakses fungsi atau data tanpa otorisasi.
**Contoh Praktik:**
```bash
curl https://hackable-pentest.vercel.app/admin
```
**Tujuan:** Lihat apakah halaman admin dapat diakses tanpa login atau autentikasi.

### A02 - Cryptographic Failures
**Deskripsi:** Enkripsi tidak digunakan dengan benar atau data penting tidak diamankan.
**Contoh Praktik:**
```bash
curl -I https://hackable-pentest.vercel.app
```
**Tujuan:** Periksa header HTTPS, seperti `Strict-Transport-Security`, dan cek apakah password disimpan dalam plain text (bisa lihat dari source code atau response).

### A03 - Injection (SQLi/XSS)
**Deskripsi:** Input pengguna yang tidak tervalidasi bisa disisipkan ke query database atau HTML.
**Contoh SQL Injection:**
```bash
curl -X POST https://hackable-pentest.vercel.app/api/login -d "username=admin' -- -&password=test"
```
**Contoh XSS:**
Masukkan input:
```html
<script>alert("XSS")</script>
```
di form komentar atau input search.

### A04 - Insecure Design
**Deskripsi:** Sistem tidak didesain untuk mempertahankan ancaman umum.
**Praktik:**
- Uji brute force login tanpa rate limit.
- Login dan coba pakai kembali session token lama.

### A05 - Security Misconfiguration
**Deskripsi:** Kesalahan konfigurasi sistem (debug mode aktif, stack trace terbuka).
**Praktik:**
```bash
curl https://hackable-pentest.vercel.app/404
```
**Tujuan:** Lihat jika ada stack trace atau pesan error server.

### A06 - Vulnerable and Outdated Components
**Deskripsi:** Komponen library atau framework usang dan memiliki kerentanan.
**Praktik:**
1. Clone repositori app.
2. Jalankan:
```bash
npm audit
```
3. Cek library yang rentan.

### A07 - Identification and Authentication Failures
**Deskripsi:** Kesalahan dalam sistem otentikasi atau manajemen sesi.
**Praktik:**
- Coba brute force login.
- Coba buka dashboard dengan token yang sudah expired.

### A08 - Software and Data Integrity Failures
**Deskripsi:** Tidak ada validasi integritas terhadap software atau file konfigurasi eksternal.
**Praktik:**
- Lihat apakah file eksternal seperti CDN JS divalidasi dengan SRI (Subresource Integrity).

### A09 - Logging and Monitoring Failures
**Deskripsi:** Aktivitas berbahaya tidak tercatat dan tidak dipantau.
**Praktik:**
- Login salah berulang kali, lihat apakah ada blokir IP atau tanda logging.
- Lakukan XSS injection dan cek respons server.

### A10 - Server-Side Request Forgery (SSRF)
**Deskripsi:** Server dapat diarahkan untuk membuat permintaan ke sumber daya internal.
**Praktik:**
```bash
curl -X POST https://hackable-pentest.vercel.app/api/fetch -d "url=http://localhost:3000/admin"
```
**Tujuan:** Apakah server melakukan fetch ke URL internal atau eksternal atas input pengguna?

## 📅 3. Format Laporan Praktikum
**Judul:** Praktikum Web Hacking OWASP Top 10  
**Nama:** [Nama Mahasiswa]  
**NIM:** [12345678]  
**Kelas:** [TI-4A / Sistem Informasi]

| No | OWASP AXX | Eksploitasi                     | Tools / Teknik | Hasil     | Bukti / Screenshot |
|----|-----------|----------------------------------|----------------|-----------|---------------------|
| 1  | A01       | Akses halaman admin langsung    | curl           | Berhasil  | [lampiran]          |
| 2  | A03       | SQL Injection login             | curl           | Login OK  | [lampiran]          |
| 3  | A06       | Audit library npm               | npm audit      | Ada 3 vuln | [lampiran]         |
| 4  | A05       | Error debug saat 404            | browser        | Stack info| [lampiran]          |
| .. | ...       | ...                              | ...            | ...       | ...                 |

## 🔺 4. Rekomendasi dan Mitigasi
- Selalu lakukan validasi dan sanitasi input (gunakan whitelist)
- Gunakan HTTPS dan enkripsi pada semua data penting
- Update rutin dependency & gunakan tool seperti `npm audit`
- Gunakan session management yang aman (token expiration, regenerasi token)
- Aktifkan logging & alert monitoring (SIEM)

## ⚠️ Disclaimer
> Praktikum ini hanya dilakukan pada **aplikasi simulasi** dan **bukan untuk penggunaan terhadap sistem tanpa izin**. Melakukan eksploitasi sistem nyata tanpa otorisasi adalah tindakan ilegal dan dapat dikenai hukuman pidana.

## 🌐 Tools Pendukung
- CLI: `curl`, `sqlmap`, `nmap`
- Proxy Intercept: `Burp Suite`, `OWASP ZAP`
- Audit: `npm audit`, `yarn audit`
- Browser: `HackTools`, `Wappalyzer`, `DevTools`
