# 🛡️ Pertemuan 11: Advanced Penetration Testing & Red Teaming

**Tujuan:** Memahami metodologi simulasi serangan tingkat lanjut (Red Teaming) dan teknik pasca-eksploitasi dalam infrastruktur perusahaan.

---

## 📚 Materi Teori

### 1. Red Teaming vs Penetration Testing
- **Pentest**: Fokus mencari sebanyak mungkin celah dalam waktu tertentu.
- **Red Teaming**: Fokus pada tujuan spesifik (objektif) dan simulasi adversari nyata tanpa terdeteksi oleh Blue Team.

### 2. Lateral Movement & Pivoting
Setelah berhasil masuk ke satu komputer, hacker akan bergerak ke komputer lain dalam jaringan yang sama.
- **Pivoting**: Menggunakan komputer yang terinfeksi sebagai "jembatan" (tunnel) untuk mengakses jaringan internal yang tidak bisa diakses langsung dari internet.

### 3. Active Directory (AD) Attacks
Pusat kendali jaringan di perusahaan besar.
- **Kerberoasting**: Mencuri service tickets untuk di-crack secara offline.
- **Golden Ticket**: Membuat tiket palsu dengan hak akses Domain Admin permanen.

---

## 🛠️ Hands-on: Post-Exploitation dengan Metasploit

### 1. Pivoting dengan Autoroute
Gunakan sesi Meterpreter sebagai proxy:
```bash
# Di dalam sessions meterpreter
run autoroute -s 10.0.0.0/24

# Gunakan socks proxy untuk akses via browser/tools lain
use auxiliary/server/socks_proxy
run
```

### 2. Dumping Hashes (Mimikatz)
Mencuri kredensial dari memori Windows:
```bash
# Di sessions meterpreter (Butuh privilege SYSTEM)
load kiwi
creds_all
```

---

## 🛡️ Red Team Operational Security (OPSEC)
Seorang Red Teamer harus menghindari deteksi:
- Gunakan perintah `built-in` (misal: `whoami`, `net user`) daripada mengunggah tools asing.
- Enkripsi komunikasi C2 (Command and Control).

---

## 📖 Referensi
- **MITRE ATT&CK Framework**: [attack.mitre.org](https://attack.mitre.org/)
- **Red Team Field Manual (RTFM)** - Ben Clark
- **Active Directory Security**: [adsecurity.org](https://adsecurity.org/)
