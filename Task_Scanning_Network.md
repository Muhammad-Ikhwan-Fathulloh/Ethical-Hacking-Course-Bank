# 🌐 Tugas Eksplorasi Keamanan Jaringan - Hackable Nuxt

## 📌 Deskripsi  
Eksplorasi ini bertujuan untuk menguji **keamanan jaringan aplikasi** yang dideploy di platform cloud (Vercel) melalui pendekatan scanning dan analisis jaringan. Tools yang digunakan termasuk `ping`, `traceroute`, `nmap`, `netcat`, dan `whois`. Target adalah subdomain aplikasi pribadi yang telah dideploy dan dimiliki secara legal.

- 🌐 **Target URL**: [https://hackable-pentest.vercel.app](https://hackable-pentest.vercel.app)  
- 📁 **Repository**: [GitHub - Hackable Pentest](https://github.com/Muhammad-Ikhwan-Fathulloh/Hackable-Pentest)

---

## 🧪 Langkah Eksplorasi

### 1. 🟢 Host Discovery (Ping)
```bash
ping -c 4 hackable-pentest.vercel.app
```
**Tujuan**: Mengetahui apakah server merespons ICMP (ping).

---

### 2. 🌐 Traceroute ke Server
```bash
traceroute hackable-pentest.vercel.app
```
**Tujuan**: Mengetahui jalur dan hops yang dilalui paket dari komputer lokal ke server aplikasi.

---

### 3. 📦 Full Port Scan dengan Nmap
```bash
nmap -sS -p- hackable-pentest.vercel.app
```
**Tujuan**: Mendeteksi semua port TCP yang terbuka (biasanya hanya port 443 jika menggunakan HTTPS).

---

### 4. 🔍 Deteksi Layanan dan Versi (Service Detection)
```bash
nmap -sV hackable-pentest.vercel.app
```
**Tujuan**: Mengidentifikasi layanan yang berjalan di port terbuka (biasanya HTTPS di 443).

---

### 5. 📥 Banner Grabbing dengan Netcat
```bash
nc hackable-pentest.vercel.app 443
```
Lalu input manual:
```
HEAD / HTTP/1.1
Host: hackable-pentest.vercel.app
```

**Tujuan**: Mencoba mendapatkan banner atau respons dari server HTTPS (meskipun TLS akan mencegah teks terbaca tanpa OpenSSL).

---

### 6. 🧠 WHOIS Lookup Domain `hackable-pentest.vercel.app`
```bash
whois hackable-pentest.vercel.app
```
**Tujuan**: Mengambil informasi registrasi subdomain yang dikelola oleh Vercel.  
**Catatan**: Karena `hackable-pentest.vercel.app` adalah **subdomain**, maka WHOIS akan merujuk ke domain utama `vercel.app`. Hasil menunjukkan bahwa subdomain ini dimiliki oleh user yang mendeploy melalui platform Vercel, bukan terdaftar terpisah di registrar.

---

## 📄 Format Laporan

- Link Docs: https://docs.google.com/document/d/1IdDiTnkZXfCdaSkzwwehaL7J7tmqYKuIYuK7xl6wIBg/edit?usp=sharing

**Judul:** Laporan Eksplorasi Keamanan Jaringan - Hackable Nuxt  
**Nama:** [Nama Mahasiswa]  
**NIM:** [Nomor Induk Mahasiswa]  
**Kelas:** [Nama Kelas / Prodi]

| No | Uji                              | Tools        | Hasil Singkat                                                  | Screenshot          |
|----|----------------------------------|--------------|-----------------------------------------------------------------|---------------------|
| 1  | Host Discovery                   | ping         | [respon: diblokir / TTL / tidak merespons]                      | [lampiran img]      |
| 2  | Traceroute                       | traceroute   | [jumlah hops, delay, posisi geolokasi (jika ada)]               | [lampiran img]      |
| 3  | Port Scan                        | nmap         | [port 443 terbuka, lainnya ditutup oleh firewall]               | [lampiran img]      |
| 4  | Service Detection                | nmap -sV     | [HTTPS, CDN/proxy, software hosting (jika terdeteksi)]          | [lampiran img]      |
| 5  | Banner Grabbing                 | netcat       | [respon TLS atau error karena koneksi tidak aman]               | [lampiran img]      |
| 6  | Whois Lookup Subdomain          | whois        | [domain utama = vercel.app, subdomain dikelola via platform]    | [lampiran img]      |

---

## ✅ Kesimpulan

**Temuan:**
- Ping diblokir oleh platform (umum untuk layanan CDN/hosting modern).
- Traceroute menunjukkan distribusi jaringan global dari Vercel.
- Hanya port 443 (HTTPS) yang dibuka.
- Server menggunakan proxy/Vercel edge server, sehingga backend tidak terekspos langsung.
- Whois lookup menunjukkan bahwa subdomain dimiliki via deployment user di Vercel.

---

## ⚠️ Disclaimer
> Pengujian hanya dilakukan terhadap aplikasi **pribadi yang dimiliki sendiri**. Semua aktivitas dilakukan untuk tujuan pembelajaran dan sesuai dengan etika keamanan siber.

---

## 📌 Lisensi
MIT License – For Educational and Ethical Hacking Purposes Only.
