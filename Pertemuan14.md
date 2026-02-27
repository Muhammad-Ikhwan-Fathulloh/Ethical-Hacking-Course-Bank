# 🛡️ Pertemuan 14: CTF Challenges & Career Roadmap

**Tujuan:** Menguji seluruh kemampuan yang telah dipelajari melalui simulasi Capture The Flag (CTF) dan merencanakan langkah karir profesional serta sertifikasi di dunia cyber security.

---

## 📚 Materi Teori

### 1. Apa itu Capture The Flag (CTF)?
Kompetisi keamanan siber di mana peserta harus menemukan "Flag" (string tersembunyi) melalui eksploitasi celah.
- **Jeopardy**: Kategori terpisah (Web, Forensics, Crypto, Pwn).
- **Attack-Defense**: Menyerang server lawan sekaligus mempertahankan server sendiri.

### 2. Roadmap Karir Cyber Security
1. **Entry Level**: Security Analyst, Junior Pentester.
2. **Mid Level**: Security Consultant, Malware Analyst.
3. **Advanced**: Security Architect, CISO (Chief Information Security Officer).

### 3. Sertifikasi Utama
- **eJPT / CEH**: Pemula / Dasar.
- **OSCP (Offensive Security)**: Emas standar untuk penetration tester (praktikal).
- **CISSP**: Fokus pada manajemen dan strategi keamanan tingkat lanjut.

---

## 🛠️ Hands-on: Final Lab Challenge

### 1. Platform Latihan Terbaik
Latih skill Anda di platform berikut yang menyediakan mesin virtual rentan:
- **TryHackMe**: Sangat ramah bagi pemula (Guided Labs).
- **HackTheBox**: Menengah ke atas (Real-world scenarios).
- **VulnHub**: Download VM rentan untuk dijalankan di VirtualBox lokal.

### 2. Tips Memenangkan CTF
- **Write-ups**: Baca laporan orang lain setelah kompetisi selesai untuk belajar trik baru.
- **Automation**: Buat script bash/python untuk tugas berulang.
- **Notes**: Simpan "Command Cheat Sheet" Anda sendiri.

---

## 🐳 Step-by-Step: Docker Kali Linux Lab (Final Challenge Prep)
Siapkan lingkungan CTF Anda secara instan di dalam container:

1.  **Persiapan**: Pastikan komputer memiliki koneksi internet yang kuat untuk mengunduh banyak paket.
2.  **Jalankan Container**: Gunakan mode host agar semua alat networking berjalan lancar:
    ```bash
    docker run -it --rm --net=host kalilinux/kali-rolling /bin/bash
    ```
3.  **Update & Install**: Instal toolset lengkap untuk berbagai kategori CTF:
    ```bash
    apt update && apt install -y nmap metasploit-framework sqlmap john aircrack-ng
    ```
4.  **Verifikasi**: Tes tool favorit Anda (misal `nmap` atau `sqlmap`) untuk memastikan siap tempur.
5.  **Eksplorasi**: Gunakan lingkungan ini untuk menyelesaikan tantangan di platform seperti **TryHackMe** atau **HackTheBox**.

## ⚖️ Etika Profesional
Menjadi hacker hebat tanpa etika hanya akan membawa Anda ke penjara. Selalu ingat:
1. **Punya Izin**: Jangan pernah mengetes sistem tanpa izin tertulis.
2. **Jangan Merusak**: Tujuan kita adalah mengamankan, bukan menghancurkan.
3. **Rahasiakan Data**: Jaga integritas data klien atau organisasi.

---

## 📖 Referensi
- **CTFTime**: [Jadwal Kompetisi CTF Global](https://ctftime.org/)
- **TryHackMe Learning Path**: [Pre-Security & Jr. Pentester](https://tryhackme.com/)
- **CyberSeek**: [Statistik Karir Cyber Security](https://www.cyberseek.org/pathway.html)
