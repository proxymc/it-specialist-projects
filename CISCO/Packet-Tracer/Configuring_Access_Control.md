# Packet Tracer - Configure Access Control

## Objectives

- **Part 1:** Configure and Use AAA Authentication Credentials
- **Part 2:** Configure and Use Email Services
- **Part 3:** Configure and Use FTP Services

## Background / Scenario

Authentication and authorization are distinct security processes in identity and access management (IAM). Authentication confirms a user's identity using passwords and other identification methods, while authorization assigns user permissions to resources.

In this Packet Tracer activity, authentication and authorization will be configured for network services including wireless network access, email, and FTP services.


---
### Part 1: Configure and Use AAA Authentication Credentials

#### Step 1: Configure user accounts on the AAA server

1. Navigate to **Headquarters** and click **Wiring Closet** (the tall, black server chassis in the bottom left corner).
2. On the right-side Rack, click **AAA-RADIUS server** > `Services` tab > `AAA` under `SERVICES`.
3. Turn on the **AAA service**.
4. Under `User Setup`, add the following usernames and passwords:

   | Username | Password |
   |----------|------------|
   | user1    | PASSuser1! |
   | user2    | PASSuser2! |

#### Step 2: Configure wireless authentication on HQ-Laptop-1

1. Navigate back to **HQ** and click **HQ-Laptop-1**.
2. Click `Config` tab > `Wireless0` under `INTERFACE`.
3. In the **SSID** box, type `HQ-INT`.
4. In the **Authentication** area, select `WPA2`.
5. Enter the following credentials:
   - **User ID:** `user1`
   - **Password:** `PASSuser1!`
6. Under **IP Configuration**, select `DHCP` and wait for the DHCP offer to be accepted.
7. Verify HQ-Laptop-1 received an IP address in the `192.168.50.0/24` network.

#### Step 3: Configure wireless authentication on HQ-Laptop-2

1. Click **HQ-Laptop-2**.
2. Repeat the steps above, using the `user2` credentials.
3. Verify HQ-Laptop-2 received an IP address in the `192.168.50.0/24` network.

---

### Part 2: Configure and Use Email Services

#### Step 1: Activate email services and configure user accounts

1. Navigate to **Wiring Closet**.
2. On the right-side Rack, click **Mail server** > `Services` tab > `EMAIL` under `SERVICES`.
3. Turn on **SMTP** and **POP3** services.
4. Set the domain to `mail.cyberhq.com`.
5. Add the following users:

   | Username | Password |
   |----------|------------|
   | HQuser1  | Cisco123!  |
   | HQuser2  | Cisco123~  |
   | BRuser1  | Cisco123-  |
   | BRuser2  | Cisco123+  |

#### Step 2: Configure email clients

| Device        | Your Name | Email Address                | User Name | Password  |
|--------------|-----------|------------------------------|-----------|------------|
| PC 1-1      | Suk-Yi    | HQuser1@mail.cyberhq.com    | HQuser1   | Cisco123!  |
| PC 2-3      | Ajulo     | BRuser1@mail.cyberhq.com    | BRuser1   | Cisco123-  |
| HQ-Laptop-1 | Malia     | BRuser2@mail.cyberhq.com    | BRuser2   | Cisco123+  |
| Net-Admin   | Cisco     | HQuser2@mail.cyberhq.com    | HQuser2   | Cisco123~  |

#### Step 3: Send an email as Suk-Yi

1. On **PC 1-1**, open `Email` under the `Desktop` tab.
2. Click `Compose` and send an email to `Ajulo (BRuser1@mail.cyberhq.com)`.
3. Navigate to **PC 2-3**, open `Email`, and click `Receive` to check the email.

---

### Part 3: Configure and Use FTP Services

#### Step 1: Activate the FTP Service

1. Navigate to **Wiring Closet**.
2. On the right-side Rack, click **FTP server** > `Services` tab > `FTP` under `SERVICES`.
3. Turn on the **FTP service**.

#### Step 2: Create FTP user accounts

| Username | Password  | User Privileges |
|----------|------------|-----------------|
| sukyi    | cisco123  | RWDNL (Write, Read, Delete, Rename, List) |
| ajulo    | cisco321  | RWDNL (Write, Read, Delete, Rename, List) |
| malia    | cisco123  | RWNL (Write, Read, Rename, List) |

#### Step 3: Transfer files between Net-Admin and the FTP server

1. Open `Command Prompt` on **Net-Admin PC**.
2. Enter:
   ```bash
   ftp 192.168.75.2
   ```
3. Authenticate with:
   ```bash
   Username: sukyi
   Password: cisco123
   ```
4. Enter `dir` to list files on the FTP server.
5. Download `aMessage.txt`:
   ```bash
   get aMessage.txt
   ```
6. Quit the FTP session, then open `Text Editor` and view the file.

   **File contents:**
   ```
   Greetings. You have successfully accessed the FTP server.
   ```
7. Create a new file, type a message, and save it as `aMessage_new.txt`.
8. Reconnect to the FTP server and upload the file:
   ```bash
   put aMessage_new.txt
   ```

#### Step 4: Verify FTP user privileges

1. Log into the FTP server from **HQ-Laptop-1** with `malia` credentials:
   ```bash
   ftp 192.168.75.2
   ```
2. Attempt to delete `aMessage_new.txt`:
   ```bash
   delete aMessage_new.txt
   ```
   - **Expected Result:** Malia cannot delete the file due to insufficient permissions.

3. Attempt to rename the file:
   ```bash
   rename aMessage_new.txt aMessage_rename.txt
   ```
   - **Expected Result:** Malia can rename the file since renaming is permitted.

4. Quit the FTP session.

---

## Conclusion

This Packet Tracer activity covered configuring and using AAA authentication credentials, email services, and FTP services. Through this lab, authentication and authorization principles were applied to enhance network security.


