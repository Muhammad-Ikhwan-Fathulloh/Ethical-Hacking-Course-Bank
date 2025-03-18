# Pertemuan 3: Passive & Active Reconnaissance (Footprinting)

## Tujuan
Memahami dan menguasai teknik pengumpulan informasi tentang target sebelum melakukan serangan melalui passive dan active reconnaissance.

---
## Materi Teori

### 1. OSINT (Open Source Intelligence)
OSINT adalah teknik pengumpulan informasi menggunakan sumber daya yang tersedia secara publik, seperti situs web, media sosial, basis data, dan forum.

### 2. WHOIS Lookup, DNS Enumeration, Google Dorking
- **WHOIS Lookup**: Digunakan untuk mendapatkan informasi domain seperti pemilik, kontak, dan server names.
- **DNS Enumeration**: Proses mendapatkan informasi tentang infrastruktur DNS suatu target, seperti subdomain dan rekaman DNS.
- **Google Dorking**: Memanfaatkan pencarian Google dengan operator khusus untuk menemukan informasi sensitif yang tidak diindeks dengan baik.

### 3. Passive vs. Active Reconnaissance
- **Passive Reconnaissance**: Mengumpulkan informasi tanpa melakukan interaksi langsung dengan target, misalnya melalui OSINT dan metadata.
- **Active Reconnaissance**: Melibatkan interaksi langsung dengan sistem target, seperti melakukan scanning port dan enumerasi layanan.

### 4. Email Harvesting & Metadata Extraction
- **Email Harvesting**: Teknik mengumpulkan alamat email target menggunakan alat seperti theHarvester atau pencarian OSINT.
- **Metadata Extraction**: Mengekstrak informasi dari dokumen atau gambar yang dapat memberikan wawasan tentang sistem dan individu terkait.

---
## Hands-on

### 1. Menggunakan Shodan, Maltego, dan Recon-ng
- **Shodan**: Mesin pencari untuk menemukan perangkat yang terhubung ke internet.
- **Maltego**: Alat visualisasi untuk hubungan data OSINT.
- **Recon-ng**: Framework reconnaissance yang dapat mengotomatisasi pengumpulan informasi.

### 2. WHOIS Lookup & DNS Enumeration dengan nslookup dan dig
- **WHOIS Lookup**:
  ```bash
  whois example.com
  ```
- **DNS Enumeration dengan nslookup**:
  ```bash
  nslookup -type=any example.com
  ```
- **DNS Enumeration dengan dig**:
  ```bash
  dig example.com any
  ```

---
## Referensi
- **OSINT Framework**: [https://osintframework.com/](https://osintframework.com/)
- **Practical Malware Analysis - Michael Sikorski**
