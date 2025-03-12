# Packet Tracer - Wireless Router Hardening and Security

---
## 📌 Overview  
In this lab, I worked on **securing a wireless router** by implementing best security practices. The exercise covered essential aspects of **wireless security hardening**, from securing administrative access to configuring encryption and isolating networks.  

By the end of this lab, I achieved the following objectives:  
✔ Strengthened **router access security** by changing the default credentials and disabling remote management.  
✔ Configured **secure wireless network settings** to prevent unauthorized access.  
✔ Implemented **WPA2 encryption** for secure communication between clients and the router.  
✔ Set up **guest network isolation** to restrict access between guest and home networks.  
✔ Verified **connectivity and security settings** to ensure proper configuration.  

---

## 🛠 Part 1: Securing the Wireless Router  
A **wireless router with default settings** is a security risk, as attackers can exploit weak credentials and open ports. My first step was to harden the router’s basic configuration.  

### 🔹 Changing Default Router Credentials  
The router’s **default login (admin/admin)** is well-known and can be easily guessed. To mitigate this:  
- I logged into the router's web interface (`192.168.0.1`).  
- Changed the **administrator password** to a strong one (**cisconetacadrocks!**).  
- Re-authenticated to ensure the changes took effect.  

🔍 **Lesson Learned:** A strong **router password** prevents unauthorized access and is the first layer of defense.  

### 🔹 Disabling Remote Management  
Remote management allows **external access** to the router for troubleshooting but also exposes it to attacks. To mitigate this risk:  
- I navigated to **Administration > Remote Management** and **disabled it**.  
- Saved the settings, which caused the router to reset.  
- Verified that the Home Office PC obtained a valid IP address again.  

🔍 **Lesson Learned:** Disabling **remote management** reduces attack surface by preventing unauthorized external access.  

---

## 🛠 Part 2: Configuring Wireless Security  
By default, **wireless networks** may allow anyone in range to connect, creating a security vulnerability. My goal was to ensure only **authorized users** could access the network.  

### 🔹 Enabling and Renaming SSID  
The SSID (Service Set Identifier) is the network name broadcasted by the router. Instead of using the **default name**, I configured it as follows:  
- **Enabled SSID Broadcast** (to make the network visible).  
- Renamed all three SSIDs to **HomeNet** for consistency.  

🔍 **Lesson Learned:** Hiding the SSID **does not** improve security since attackers can still detect it using **packet sniffing tools**.  

### 🔹 Implementing WPA2 Encryption  
To **protect wireless communication**, I secured all networks with **WPA2-Personal (AES encryption)**:  
- **Security Mode:** WPA2-Personal  
- **Encryption Type:** AES  
- **Passphrase:** ciscorocks  

🔍 **Lesson Learned:** **WPA2 (AES)** encryption is a **mandatory security standard**. **WEP and WPA are outdated** and vulnerable to cracking.  

### 🔹 Setting Up a Guest Network  
For visitors, I configured a **separate Guest network**:  
- **SSID:** GuestNet  
- **Security Mode:** WPA2-Personal  
- **Passphrase:** guestpass  

🔍 **Lesson Learned:** A **guest network** keeps external devices **isolated** from private resources, reducing the risk of **malware infections and unauthorized access**.  

---

## 🛠 Part 3: Configuring Wireless Clients  
With the wireless networks secured, I connected various devices.  

### 🔹 Connecting Laptops to the Secured Network  
- **Home Laptop 1** connected to **HomeNet** using `ciscorocks`.  
- **Home Laptop 2** connected to **GuestNet** using `guestpass`.  

To ensure connectivity:  
- I verified that both laptops received a **DHCP-assigned IP** from `192.168.0.0/24`.  
- Checked the **"You have successfully connected to the access point"** message.  

### 🔹 Connecting IoT Devices  
For **IoT security**, I configured the **Home Webcam, Home Siren, and Home Doors** with:  
- **SSID:** HomeNet  
- **Authentication:** WPA2-PSK  
- **Passphrase:** ciscorocks  

🔍 **Lesson Learned:** IoT devices must use **strong encryption** and **be placed on a separate VLAN** where possible.  

---

## 🛠 Part 4: Verifying Security and Connectivity  
### 🔹 Testing Internet Access  
To confirm that devices were connected securely:  
- I opened a web browser on **both laptops** and successfully loaded `www.ptsecurity.com`.  

### 🔹 Isolating Guest Network Traffic  
By default, guests could **communicate with HomeNet devices**, which is a security risk. To fix this:  
- I **disabled guest-to-home network access** in the router settings.  
- Verified that **Home Laptop 2 (GuestNet) could no longer ping Home Laptop 1 (HomeNet)**.  

🔍 **Lesson Learned:** **Network segmentation** is crucial to **prevent unauthorized access** between trusted and untrusted devices.  

---

## 💡 Final Thoughts and Key Takeaways  
This lab reinforced essential **wireless security principles** that apply to both **home** and **enterprise** environments.  

### 🔑 Key Takeaways:  
✔ **Change default credentials** immediately to prevent unauthorized access.  
✔ **Disable remote management** to reduce attack exposure.  
✔ **Always use WPA2/AES encryption** (avoid WEP and older protocols).  
✔ **Set up a separate guest network** to **isolate** external users.  
✔ **Verify network segmentation** to prevent **lateral movement** in case of a breach.  

By securing the router and implementing these **best practices**, I gained hands-on experience in **wireless security hardening**, an essential skill in **network security and IT administration**.  

---
#### 🔙 [Back To CISCO Labs](/CISCO/Packet-Tracer/)
#### 🔙 [Back To IT Specialist Projects Repository](https://github.com/proxymc/it-specialist-projects)  




