# Packet Tracer - Implement Physical Security with IoT Devices

## Objectives

- **Part 1:** Connect IoT Devices to the Network
- **Part 2:** Add IoT Devices to the Registration Server
- **Part 3:** Explore IoT Security Device Functionality

## Background / Scenario

To improve home security, IoT devices will be installed to allow remote monitoring. This lab involves connecting IoT devices to a wireless network, registering them with a remote server, and interacting with them via an IoT management system.

---

## Part 1: Connect IoT Devices to the Network

### Step 1: Connect the Siren to the Door
1. Click **Home** and locate **Home_Siren** and **Home Doors** in the living room.
2. Select **Connections > IoT Custom Cable** from the toolbar.
3. Connect **Home_Siren (DO interface)** to **Home Doors (DO interface)**.
4. Hold the **ALT key** and click the door to open and close it.
   - The siren will activate when the door is opened.

### Step 2: Associate IoT Devices to HomeNet Wireless Network
The **Home Wireless Router** is pre-configured with **WPA2-PSK** and **MAC Address Filtering**.

#### IoT Devices:
- **Home_Siren**
- **Home Doors**
- **Home_Motion_Sensor** (home office windows)
- **Home_Webcam** (home office bookshelf)

#### Configuration (Example for Home_Siren)
1. Click **Home_Siren** > **Config tab** > **Wireless0**.
2. Set:
   - **SSID:** HomeNet
   - **Authentication:** WPA2-PSK
   - **Passphrase:** ciscorocks
3. In **IP Configuration**, select **DHCP** and ensure the device gets an IP from `192.168.0.0/24`.
4. Record the **MAC address** in colon format:
   - Home_Siren: `00:90:2B:C8:C6:E2`
   - Home Doors: `00:0A:F3:DB:2E:37`
   - Home_Motion_Sensor: `00:40:0B:39:21:24`
   - Home_Webcam: `00:D0:58:D1:C4:11`
5. Repeat for all devices.

### Step 3: Configure MAC Address Filtering
1. Open **Home Office PC** > **Desktop** > **Web Browser**.
2. Login to `192.168.0.1` with **admin/admin**.
3. Navigate to **Wireless > Wireless MAC Filter**.
4. Ensure filtering is enabled for **2.4 GHz** and set to **Permit PCs**.
5. Add the MAC addresses of all IoT devices.
6. Click **Save Settings** to apply changes.

---

## Part 2: Add IoT Devices to the Registration Server

### Step 1: Create an Account
1. On **Home Office PC**, open **Web Browser**.
2. Navigate to `http://10.3.0.125`.
3. Click **Sign up now** and create an account:
   - **Username:** HomeUser
   - **Password:** Pa$$w0rd

### Step 2: Register IoT Devices with the Server
Each IoT device must be registered for remote monitoring.

#### Configuration (Example for Home_Siren)
1. Click **Home_Siren** > **Config tab** > **Settings (Global)**.
2. Under **IoT Section**:
   - **Select Remote Server**
   - **Server Address:** `10.3.0.125`
   - **Username:** HomeUser
   - **Password:** Pa$$w0rd`
3. Click **Connect**. The button should change from **Connecting** to **Refresh**.
4. Repeat for all IoT devices.

### Step 3: Verify Registration
1. Open **Web Browser** on **Home Office PC**.
2. Login to `10.3.0.125` with **HomeUser/Pa$$w0rd**.
3. Confirm all devices appear as **registered**.

---

## Part 3: Explore IoT Security Device Functionality

### Step 1: Observe and Control Devices from the Registration Server

| Action | Expected Outcome |
|--------|-----------------|
| View device status | All devices should be **On** |
| Click red rectangle under Home Doors | Siren and door indicators turn **green**, door opens, siren activates |
| Click door rectangle again | Siren and door indicators turn **red**, siren deactivates |
| Click green rectangle for Home_Webcam | Video feedback turns **off** |
| Click green rectangle again for Home_Webcam | Video feedback turns **on** |
| Click red circle for Home_Motion_Sensor | No change, as it only sends data |

### Step 2: Interact with Sensors in the Home

| Action | Expected Outcome |
|--------|-----------------|
| **ALT-Click on the door** | Door and siren activate, status updates on server |
| **ALT-Click on the webcam** | Webcam turns **off**, server reflects change |
| **ALT + Move mouse over Motion Sensor** | Motion detected, activity light turns **green** on server |

---

## Reflection Questions

**1. What advantages do IoT devices provide for home security?**
- IoT devices are **easy to install and configure**.
- They integrate with **home network security techniques**.
- Allow **remote monitoring and automation** of security systems.

**2. What is the advantage of using a registration server for IoT devices?**
- Provides **remote access** to monitor and control devices.
- Enables **video surveillance** and **real-time monitoring**.

**3. What types of IoT devices are used for home security?**
- Fire alarms
- Video monitoring devices
- Entry alarms
- Motion sensors
- Water sensors
- Device monitoring systems

---

## Conclusion
This lab demonstrated how to configure and secure IoT devices within a home network. By connecting IoT devices to a **wireless network**, **configuring MAC filtering**, **registering with a remote server**, and **remotely managing them**, we established a secure and efficient home security system.

