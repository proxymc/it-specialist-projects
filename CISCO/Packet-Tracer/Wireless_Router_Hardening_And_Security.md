# 🛡 Packet Tracer - Configure Wireless Router Hardening and Security  

## 📌 Overview  
This lab focuses on **securing a wireless router** by implementing best security practices, including:  
✔ Changing default router credentials  
✔ Disabling remote management  
✔ Configuring WPA2 encryption  
✔ Enforcing guest network isolation  

📂 **Full Lab Write-Up:** [Packet-Tracer-Wireless-Router-Security.md](./Packet-Tracer-Wireless-Router-Security.md)  

## 🔧 Part 1: Configure Basic Security Settings  
### 🔹 Changing Default Router Password  
- Accessed **192.168.0.1** via a browser  
- Logged in with default credentials: `admin / admin`  
- Changed password to **cisconetacadrocks!**  

### 🔹 Disabling Remote Management  
- Disabled **Remote Management** under the Administration tab  
- This prevents external access and mitigates password brute-force attacks  

## 📡 Part 2: Configure Wireless Router Network Security  
### 🔹 Broadcasting the SSID  
- Enabled SSID broadcast for all networks  
- Set the **SSID name** to **HomeNet**  
- SSID hiding is not an effective security measure  

### 🔹 Configuring WPA2 Encryption  
- Applied **WPA2-Personal (AES)** for all networks  
- Set **passphrase** to **ciscorocks** for HomeNet  
- Ensured **GuestNet** uses **WPA2-PSK** with password **guestpass**  

## 💻 Part 3: Secure Wireless Clients  
### 🔹 Connecting Home Laptops  
- Connected **Home Laptop 1** to **HomeNet** (password: `ciscorocks`)  
- Connected **Home Laptop 2** to **GuestNet** (password: `guestpass`)  
- Verified DHCP assigned IP addresses correctly  

### 🔹 Configuring IoT Devices  
- Connected **Home_Webcam, Home_Siren, and Home_Doors** to **HomeNet**  
- Used **WPA2-PSK authentication**  

## 🔍 Part 4: Verify Security & Connectivity  
### 🔹 Internet Access Check  
- Opened **www.ptsecurity.com** from Home Laptop 1 & 2  
- Verified successful page load  

### 🔹 Isolating Guest Network  
- **Before:** Home Laptop 2 could ping Home Laptop 1  
- **After:** Disabled **"Allow guests to access local network"** in router settings  
- **Result:** Home Laptop 2 could no longer access internal devices  

## 🎯 Key Takeaways  
✔ Default credentials & remote access are major security risks  
✔ WPA2-AES encryption is essential for wireless security  
✔ Guest networks should be **isolated** from internal devices  
✔ Always verify security settings with **connectivity tests**  



