# Ethical-Hacking-Course-Bank 🛡️
Bank Materi dan Praktikum Kuliah Ethical Hacking.

---

## **📍 Daftar Isi**
- [Minggu 1-2: Dasar-Dasar Ethical Hacking](#-minggu-1-2-dasar-dasar-ethical-hacking)
  - [Pertemuan 1: Pengenalan Ethical Hacking & Cybersecurity](#-pertemuan-1-pengenalan-ethical-hacking--cybersecurity)
  - [Pertemuan 2: Linux & Networking Fundamentals](#-pertemuan-2-linux--networking-fundamentals-untuk-hacking)
- [Minggu 3-4: Information Gathering & Scanning](#-minggu-3-4-information-gathering--scanning)
  - [Pertemuan 3: Passive & Active Reconnaissance](#-pertemuan-3-passive--active-reconnaissance-footprinting)
  - [Pertemuan 4: Scanning & Enumeration](#-pertemuan-4-scanning--enumeration)
- [Minggu 5-6: Eksploitasi Sistem & Akses Tidak Sah](#-minggu-5-6-eksploitasi-sistem--akses-tidak-sah)
- [Minggu 7-8: Password Cracking & Wireless Hacking](#-minggu-7-8-password-cracking--wireless-hacking)
- [Minggu 9-14: Advanced Attacks, Penetration Testing & Defense](#-minggu-9-14-advanced-attacks-penetration-testing--defense)

---

## **📅 Minggu 1-2: Dasar-Dasar Ethical Hacking**

### **🛡️ [Pertemuan 1: Pengenalan Ethical Hacking & Cybersecurity](Pertemuan1.md)**
**Tujuan:** Memahami konsep dasar ethical hacking dan perannya dalam keamanan siber.

#### **Materi Teori:**
- Definisi dan peran ethical hacking
- Jenis hacker: White Hat, Black Hat, Grey Hat
- Perbedaan Ethical Hacking dan Cybercrime
- Hukum & Regulasi (GDPR, NIST, ISO 27001, UU ITE)
- Tahapan hacking: Reconnaissance, Scanning, Gaining Access, Maintaining Access, Covering Tracks
- Pengenalan sertifikasi: CEH, OSCP, CISSP, PenTest+

#### **Hands-on:**
- Instalasi Kali Linux di VirtualBox/VMware/Docker/WSL
- Simulasi dasar terminal menggunakan Kali Linux

#### **Referensi:**
- EC-Council: Certified Ethical Hacker (CEH) v12
- NIST Cybersecurity Framework
- OWASP Top 10

---

### **🛡️ [Pertemuan 2: Linux & Networking Fundamentals untuk Hacking](Pertemuan2.md)**
**Tujuan:** Menguasai dasar-dasar sistem operasi dan jaringan untuk penetration testing.

#### **Materi Teori:**
- Dasar-dasar Linux Command Line (CLI)
- Struktur file Linux & User Privileges
- TCP/IP, Ports, Protocols, dan Model OSI
- Wireshark untuk sniffing traffic
- Virtualization & lab setup dengan VMware/VirtualBox

#### **Hands-on:**
- Navigasi terminal Linux (ls, cd, nano, chmod, sudo, grep)
- Analisis lalu lintas jaringan dengan Wireshark

#### **Referensi:**
- The Linux Command Line - William Shotts
- Nmap Network Scanning - Gordon "Fyodor" Lyon

---

## **📅 Minggu 3-4: Information Gathering & Scanning**

### **🛡️ [Pertemuan 3: Passive & Active Reconnaissance (Footprinting)](Pertemuan3.md)**
**Tujuan:** Mengumpulkan informasi tentang target sebelum melakukan serangan.

#### **Materi Teori:**
- OSINT (Open Source Intelligence)
- WHOIS lookup, DNS Enumeration, Google Dorking
- Passive vs. Active Reconnaissance
- Email Harvesting & Metadata Extraction

#### **Hands-on:**
- Menggunakan **Shodan, Maltego, Recon-ng** untuk mencari informasi target
- WHOIS lookup & DNS Enumeration dengan **nslookup dan dig**

---

### **🛡️ [Pertemuan 4: Scanning & Enumeration](Pertemuan4.md)**
**Tujuan:** Mengidentifikasi layanan dan kerentanan di target.

#### **Materi Teori:**
- **Nmap** untuk scanning jaringan
- Enumerasi dengan **Netcat & Enum4linux**
- Banner Grabbing & Fingerprinting OS
- Web scanning dengan **Nikto & Dirb**

#### **Hands-on:**
- Scanning jaringan dengan Nmap
- Melakukan enumerasi layanan menggunakan Netcat

---

## **📅 Minggu 5-6: Eksploitasi Sistem & Akses Tidak Sah**

### **🛡️ Pertemuan 5: Vulnerability Assessment & Exploitation Basics**
**Tujuan:** Memahami cara mengeksploitasi kerentanan sistem.

#### **Materi Teori:**
- CVE & Exploit Database (Exploit-DB, CVE, NVD)
- Buffer Overflow & Code Injection
- Penggunaan Metasploit Framework
- Exploited SMB, FTP, dan RDP

#### **Hands-on:**
- Eksploitasi dengan **Metasploit** terhadap sistem rentan

---

### **🛡️ Pertemuan 6: Web Application Hacking (OWASP Top 10)**
**Tujuan:** Mengenali dan mengeksploitasi kelemahan aplikasi web.

#### **Materi Teori:**
- SQL Injection (SQLi)
- Cross-Site Scripting (XSS)
- Cross-Site Request Forgery (CSRF)
- Broken Authentication & Session Hijacking

#### **Hands-on:**
- SQL Injection & XSS exploitation menggunakan DVWA (Damn Vulnerable Web App)

---

## **📅 Minggu 7-8: Password Cracking & Wireless Hacking**

### **🛡️ Pertemuan 7: Password Cracking & Privilege Escalation**
**Tujuan:** Memahami cara membobol password dan meningkatkan hak akses.

#### **Materi Teori:**
- Brute Force & Dictionary Attack (Hydra, John The Ripper)
- Windows & Linux Privilege Escalation
- Token Hijacking & Pass-the-Hash attack

#### **Hands-on:**
- Cracking password dengan John the Ripper

---

### **🛡️ Pertemuan 8: Wireless Network Hacking**
**Tujuan:** Menguji keamanan Wi-Fi dan eksploitasi jaringan nirkabel.

#### **Materi Teori:**
- Jenis enkripsi Wi-Fi (WEP, WPA, WPA2, WPA3)
- Serangan Evil Twin & Rogue Access Point
- Wi-Fi Sniffing dengan Airodump-ng

#### **Hands-on:**
- Cracking WPA2 Wi-Fi dengan Aircrack-ng

---

## **📅 Minggu 9-14: Advanced Attacks, Penetration Testing & Defense**

### **🛡️ Pertemuan 9: Advanced Persistent Threats (APT) & Social Engineering**
**Tujuan:** Memahami teknik serangan jangka panjang dan manipulasi psikologis.

#### **Materi Teori:**
- Anatomy of an APT attack
- Phishing, Spear Phishing, Vishing, Smishing
- Social Engineering Toolkit (SET)

#### **Hands-on:**
- Simulasi serangan phishing menggunakan SET

---

### **🛡️ Pertemuan 10-14: Advanced Attacks, Incident Response, & Defense**

### **🛡️ Pertemuan 10: Malware Analysis & Reverse Engineering**
**Tujuan:** Memahami karakteristik malware dan cara menganalisisnya secara aman.

#### **Materi Teori:**
- Jenis-jenis Malware (Virus, Worm, Trojan, Ransomware, Spyware)
- Static Analysis: Menganalisis kode tanpa menjalankannya
- Dynamic Analysis: Mengamati perilaku malware di lingkungan Sandbox
- Reverse Engineering: Membongkar binary menggunakan **Ghidra atau IDA Pro**

#### **Hands-on:**
- Analisis file mencurigakan dengan **VirusTotal & PeStudio**
- Deteksi malware sederhana di lingkungan lab

---

### **🛡️ Pertemuan 11: Advanced Penetration Testing & Red Teaming**
**Tujuan:** Memahami metodologi simulasi serangan tingkat lanjut dan operasi Red Team.

#### **Materi Teori:**
- Red Teaming vs. Penetration Testing
- Lateral Movement & Pivoting
- Post-Exploitation dengan **PowerShell Empire atau Cobalt Strike**
- Active Directory Attacks (Kerberoasting, Golden Ticket)

#### **Hands-on:**
- Simulasi lateral movement di lab Windows AD
- Penggunaan alat post-exploitation

---

### **🛡️ Pertemuan 12: Incident Response & Digital Forensics**
**Tujuan:** Mampu merespon insiden keamanan dan melakukan investigasi digital.

#### **Materi Teori:**
- Incident Response Life Cycle (NIST: Preparation, Detection, Containment, Eradication, Recovery)
- Dasar Digital Forensics: Integrity, Chain of Custody
- Analisis memori (RAM Forensics) dan disk forensics
- Log Analysis (SIEM & EDR)

#### **Hands-on:**
- Investigasi artefak Windows dengan **Autopsy**
- Analisis memory dump menggunakan **Volatility**

---

### **🛡️ Pertemuan 13: Security Hardening & Blue Team Strategies**
**Tujuan:** Mengimplementasikan strategi pertahanan untuk mengamankan infrastruktur.

#### **Materi Teori:**
- Prinsip Defense in Depth
- Network Security: Firewall (PFSense), IDS/IPS (Snort/Suricata)
- Endpoint Security: Antivirus, EDR, Hardening OS
- Monitoring & Log Management (ELK Stack/Splunk)

#### **Hands-on:**
- Konfigurasi Rule Firewall dasar
- Hardening server Linux & Windows

---

### **🛡️ Pertemuan 14: Capture The Flag (CTF) Challenge & Sertifikasi Ethical Hacking**
**Tujuan:** Menguji kemampuan melalui tantangan CTF dan merencanakan karir profesional.

#### **Materi Teori:**
- Jenis tantangan CTF: Jeopardy vs Attack-Defense
- Platform latihan: TryHackMe, HackTheBox, VulnHub
- Roadmap Karir: Sertifikasi (CEH, OSCP, eJPT, CISSP)
- Etika Profesional bagi Ethical Hacker

#### **Hands-on:**
- Final Lab Challenge: Menemukan flag di mesin yang sudah disediakan

---
_Dikelola oleh: Muhammad Ikhwan Fathulloh_