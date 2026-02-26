# 🛡️ Pertemuan 13: Security Hardening & Blue Team Strategies

**Tujuan:** Mengimplementasikan strategi pertahanan berlapis (Defense in Depth) dan teknik hardening pada peladen (server) untuk meminimalkan permukaan serangan.

---

## 📚 Materi Teori

### 1. Prinsip Defense in Depth
Keamanan tidak boleh mengandalkan satu alat saja. Jika satu lapisan ditembus, lapisan lain harus tetap melindungi data.
- **Data Layer**: Enkripsi DB.
- **Application Layer**: Web Application Firewall (WAF).
- **Network Layer**: Firewalls, IDS/IPS.
- **Physical Layer**: CCTV, Biometric.

### 2. IDS vs IPS (Network Security)
- **IDS (Intrusion Detection System)**: Memantau dan memberi peringatan (Alert) jika ada trafik mencurigakan (contoh: Snort).
- **IPS (Intrusion Prevention System)**: Memantau dan langsung **memblokir** trafik berbahaya.

---

## 🛠️ Hands-on: Hardening System

### 1. Konfigurasi Firewall Dasar (UFW di Linux)
UFW (Uncomplicated Firewall) adalah cara mudah mengelola aturan trafik.
```bash
# Aktifkan firewall
sudo ufw enable

# Izinkan SSH dan HTTP
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp

# Lihat status
sudo ufw status verbose
```

### 2. Hardening SSH
Ubah konfigurasi di `/etc/ssh/sshd_config`:
- `Port 2222`: Ubah port default (Security by Obscurity).
- `PermitRootLogin no`: Melarang login langsung sebagai root via SSH.
- `PasswordAuthentication no`: Gunakan **SSH Key** alih-alih password.

### 3. Monitoring Log (Fail2Ban)
Automasi pemblokiran IP yang mencoba Brute Force SSH.
```bash
# Install Fail2Ban
sudo apt install fail2ban -y

# Fail2Ban akan otomatis memantau /var/log/auth.log 
# dan memblokir IP setelah beberapa kali gagal login.
```

---

## 🔍 Blue Team Monitoring
Gunakan SIEM (Security Information and Event Management) seperti **ELK Stack** (Elasticsearch, Logstash, Kibana) untuk memantau trafik dari seluruh jaringan di satu dashboard pusat.

---

## 📖 Referensi
- **CIS Benchmarks**: [Standard Global Security Configuration](https://www.cisecurity.org/benchmark)
- **SANS Blue Team Cheat Sheets**: [Blue Team Handbook](https://www.sans.org/blog/tags/blue-team/)
- **Practical Blue Team** - Don Murdoch
