# Packet Tracer - Wireless Router Hardening and Security
---

## 📌 OVERVIEW 
This lab focuses on **hardening a wireless router** to enhance security and mitigate potential attacks. By configuring the router’s basic security settings, wireless security, and client connectivity, we create a more resilient home network. 

### **Objectives**  
1. Configure basic security settings for a wireless router.  
2. Configure wireless router network security.  
3. Configure wireless clients' network security.  
4. Verify connectivity and security settings.  

---

## **🛠 Part 1: Configure Basic Security Settings for a Wireless Router**

The default settings on a wireless router can pose a security risk, making it essential to change login credentials and disable remote management.

### [Wide Network Visualisation Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/Packet-Tracer/Images/Wireless_Router_Hardening_And_Security/Packet%20Tracer%20Configure%20Wireless%20Router%20Hardening%20and%20Security.png)
### [Home Network Visualisation Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/Packet-Tracer/Images/Wireless_Router_Hardening_And_Security/Packet%20Tracer%20Home.png)

### **Step 1: Change the Default Router Password**
1. Click **Home Office PC** > `Desktop` tab > **Web Browser**.  
2. Connect to the **Home Wireless Router** at `192.168.0.1`.  
3. Log in with:
   - **Username:** admin  
   - **Password:** admin  
4. Navigate to the **Administration** tab.  
5. Change the password to `cisconetacadrocks!` in both fields.  
6. Click **Save Settings** and re-authenticate using the new credentials.  

### [Changing Default Password Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/Packet-Tracer/Images/Wireless_Router_Hardening_And_Security/Changing%20Default%20Password%20.png)

### **Step 2: Disable Remote Management**
1. Navigate to the **Administration** tab.  
2. Set `Remote Management` to **Disabled**.  
3. Click **Save Settings**.  
4. Allow the router to reset, then reconnect using the browser at `192.168.0.1`.  
5. Verify that **Home Office PC** receives an IP address from `192.168.0.1/24` network.

### [Veryfying Home Office PC Connection Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/Packet-Tracer/Images/Wireless_Router_Hardening_And_Security/Changing%20Default%20Password2.png)

---

## **🔒 Part 2: Configure Wireless Router Network Security**
By default, wireless networks may be accessible to unauthorized users. We will secure these networks by enabling encryption and configuring SSIDs.

### **Step 1: Configure and Broadcast the SSID**
1. Navigate to the **Wireless** tab.  
2. Enable `SSID Broadcast` for all three networks.  
3. Change each SSID name to `HomeNet`.  
4. Click **Save Settings**.  

### **Step 2: Configure Security for HomeNet**
1. In the **Wireless** tab, go to **Wireless Security**.  
2. For each of the three networks:
   - **Security Mode:** WPA2 Personal  
   - **Encryption:** AES  
   - **Passphrase:** `ciscorocks`  
3. Click **Save Settings**.

### [Configuring Security for HomeNet Image](https://github.com/proxymc/it-specialist-projects/blob/main/CISCO/Packet-Tracer/Images/Wireless_Router_Hardening_And_Security/Best%20security%20for%20the%20HomeNet%20Wireless%20Networks.png)

### **Step 3: Configure Security for GuestNet**
1. Go to the **Wireless** tab > **Guest Network**.  
2. Enable `Guest Profile` for all three networks and configure:
   - **SSID:** GuestNet  
   - **SSID Broadcast:** Enabled  
   - **Security Mode:** WPA2 Personal  
   - **Encryption:** AES  
   - **Passphrase:** `guestpass`  
3. Click **Save Settings**.

### [Configuring Security for GuestNet Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/Packet-Tracer/Images/Wireless_Router_Hardening_And_Security/Best%20security%20for%20GuestNet%20Wireless%20Networks.png)
---

## **💻 Part 3: Configure Wireless Clients Network Security**
After securing the wireless router, we connect client devices using the appropriate security settings.

### **Step 1: Connect Laptops to HomeNet and GuestNet**
1. Click **Home Laptop 1** > `Desktop` > **PC Wireless**.  
2. Select **HomeNet** and click **Connect**.  
3. Enter `ciscorocks` as the Pre-shared Key.  
4. Verify successful connection under **Link Information**.  
5. Repeat for **Home Laptop 2**, but connect to **GuestNet** with the passphrase `guestpass`.  

### [Connecting Laptops To Network Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/Packet-Tracer/Images/Wireless_Router_Hardening_And_Security/Home%20Laptop%201%20Wirless%20Connection.png)

### **Step 2: Connect IoT Devices**
1. Click **Home_Webcam** > `Config` > `Wireless0`.  
2. Set **SSID** to `HomeNet`.  
3. Choose **WPA2-PSK** authentication and enter `ciscorocks`.  
4. Set `IP Configuration` to **DHCP**.  
5. Repeat for **Home_Siren** and **Home_Doors**.

### [Configuring WebCam Connection](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/Packet-Tracer/Images/Wireless_Router_Hardening_And_Security/Home%20Web%20Cam%20connectivity%20configuration.png)

---

## **✅ Part 4: Verify Connectivity and Security Settings**
After configuration, we test connectivity and enforce network isolation.

### **Step 1: Test Internet Connectivity**
1. Click **Home Laptop 1** > `Desktop` > **Web Browser**.  
2. Navigate to `www.ptsecurity.com` to confirm internet access.  
3. Repeat for **Home Laptop 2**.

### **Step 2: Prevent GuestNet from Accessing HomeNet**
1. Find the IP address of **Home Laptop 1**.  
2. On **Home Laptop 2**, open `Command Prompt` and enter:
   ```sh
   ping [Home Laptop 1's IP]
   ```

### [Confirming Communication Of Devices On Local Network Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/Packet-Tracer/Images/Wireless_Router_Hardening_And_Security/Guest%20Network%20And%20Home%20Network%20Laptops%20communicate.png)

3. If pings succeed, restrict interconnectivity:
   - Go to `192.168.0.1`, **Wireless** > **Guest Network**.
   - Uncheck `Allow guests to see each other and access the local network`.
   - Click **Save Settings**.
4. Repeat the `ping` test from **Home Laptop 2**—the request should now fail.

### [Local Communcation Disconected Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/Packet-Tracer/Images/Wireless_Router_Hardening_And_Security/Guest%20Network%20And%20Home%20Network%20Laptops%20communicate.png)

---

## **📚 Lessons Learned**
- **Changing default credentials** is the first step to securing any network device.
- **Remote management** should be disabled unless absolutely necessary.
- **WPA2 encryption with AES** is essential for protecting wireless traffic.
- **Guest networks** should be isolated from the main network.
- **Proper IP allocation** (using DHCP) ensures smooth connectivity for all devices.

By following these best practices, we significantly reduce security risks and ensure a **safe and reliable** wireless network. 🔐


---
#### 🔙 [Back To CISCO Labs](/CISCO/Packet-Tracer/)
#### 🔙 [Back To IT Specialist Projects Repository](https://github.com/proxymc/it-specialist-projects)  




