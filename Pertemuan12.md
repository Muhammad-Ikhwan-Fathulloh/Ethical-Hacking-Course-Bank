# 🛡️ Pertemuan 12: Incident Response & Digital Forensics

**Tujuan:** Memahami prosedur penanganan insiden keamanan siber dan dasar-dasar investigasi digital (forensik) untuk mengidentifikasi pelaku serangan.

---

## 📚 Materi Teori

### 1. Incident Response Life Cycle (NIST)
Siklus standar untuk menangani serangan:
1. **Preparation**: Menyiapkan tools dan tim.
2. **Detection & Analysis**: Mengidentifikasi serangan sedang terjadi.
3. **Containment & Eradication**: Mengisolasi target dan menghapus malware.
4. **Recovery**: Mengembalikan sistem ke kondisi normal.
5. **Post-Incident Activity**: Evaluasi dan perbaikan (Lesson Learned).

### 2. Dasar Digital Forensics
- **Integrity**: Data bukti tidak boleh berubah bit sedikitpun.
- **Chain of Custody**: Dokumen yang mencatat siapa yang memegang bukti dari awal ditemukan hingga di pengadilan.
- **Volatility Order**: Ambil bukti mulai dari yang paling mudah hilang (RAM > Disk > Tape).

---

## 🛠️ Hands-on: Investigasi Artefak

### 1. Memory Forensics dengan Volatility
Menganalisis file dump RAM untuk melihat proses yang sedang berjalan saat serangan terjadi.
```bash
# Melihat info sistem dari memory dump
volatility -f mem.raw imageinfo

# Melihat daftar proses
volatility -f mem.raw --profile=Win7SP1x64 pslist
```

### 2. File Recovery & Analysis dengan Autopsy
Tool GUI gratis untuk menganalisis isi Hardisk:
- **Langkah**: Masukkan image disk, cari file yang baru dihapus, dan periksa histori browser atau file registry.

---

## 🐳 Hands-on: Docker Kali Linux
Melakukan investigasi forensik di dalam container:
```bash
# Jalankan container
docker run -it --rm kalilinux/kali-rolling /bin/bash

# Instal tools Forensik:
apt update && apt install -y volatility3 sleuthkit
```

## 🔍 Bukti Penting dalam Windows
- **Prefetch**: Mengetahui aplikasi apa saja yang pernah dijalankan.
- **Registry**: Menyimpan konfigurasi sistem dan jejak malware.
- **Event Logs**: Catatan aktivitas sistem (login, error, service restart).

---

## 📖 Referensi
- **NIST SP 800-61**: [Computer Security Incident Handling Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)
- **The Art of Memory Forensics** - Ligh, Case, Levy, & Rao
- **SANS Forensics Blog**: [digital-forensics.sans.org](https://www.sans.org/blog/category/digital-forensics/)
