# Packet Tracer - File and Data Integrity Checks

## 📌Overview
In this lab, we will verify the integrity of multiple files using hashes to ensure they have not been tampered with. If any discrepancies are found, the files will be transferred to a designated analyst for further investigation. This exercise simulates real-world cybersecurity practices for maintaining data integrity.

### Objectives

- Recover files after a cyber attack.
- Use hashing to verify file integrity.
- Use HMAC to verify file integrity.

### Resources

- **CSE-LABVM** installed in VirtualBox
- **Packet Tracer** for network simulation

---
## Instructions

### Part 1: Recover Files after a Cyber Attack

1. **Access the Branch Office Server from Mike’s PC**

   - Open the **Branch Office Laptop (BR-1)** in Packet Tracer.
   - Navigate to the **Web Browser** and enter `http://branch.corp`.
   - Download the most current files.

2. **Copy the last archived hash values**

   - Navigate to `http://hq.corp`.
   - Copy the most recent file hashes.
   - Open **CSE-LABVM**, launch **Text Editor Pluma**, and paste the copied hash values.

3. **Download backup files to Mike’s PC**

   - Connect to the **HQ FTP Server** via the command:
     ```bash
     ftp hq.corp
     ```
   - Use credentials: `mike / cisco123`
   - List available files using:
     ```bash
     dir
     ```
   - Download client files:
     ```bash
     get NEclients.txt
     get NWclients.txt
     get Nclients.txt
     get SEclients.txt
     get SWclients.txt
     get Sclients.txt
     ```
   - Verify the files have been downloaded.

### Part 2: Use Hashing to Verify File Integrity

1. **Generate hashes for the downloaded files**

   - Open **CSE-LABVM Terminal**.
   - Compute MD5 hashes:
     ```bash
     echo -n 'file-contents' | md5sum
     ```
   - Compare each generated hash with the archived hash values.
   - Identify the tampered file (e.g., `SEclients.txt`).

2. **Escalate the incident**

   - Notify **Sally (supervisor)** via email (`sally@branch.corp`).
   - Provide details on the tampered file.

3. **Transfer the tampered file to Sally's PC**

   - On **HQ-Laptop-1**, connect to the FTP server:
     ```bash
     ftp hq.corp
     ```
   - Use credentials: `sally / cisco321`
   - Download the tampered file.
   - Verify successful transfer.

### Part 3: Use HMAC to Verify File Integrity

1. **Compute an HMAC for a critical financial file**

   - On **HQ-Laptop-2**, verify the presence of `income.txt`.
   - Copy its content to **CSE-LABVM**.
   - Save the file as `income.txt`.
   - Generate an HMAC hash using the secret key `cisco123`:
     ```bash
     openssl dgst -sha256 -hmac cisco123 income.txt
     ```
   - Compare the computed HMAC with the original.

2. **Why is HMAC more secure than regular hashing?**

   - Unlike general hashing, **HMAC requires both the original message and a secret key**, making it more resistant to unauthorized modifications.

## Lessons Learned

- **File integrity checks are essential** in cybersecurity to detect unauthorized modifications.
- **MD5 hashing is a quick way** to verify file integrity, but HMAC provides additional security by requiring a secret key.
- **Incident escalation is important**—reporting compromised files ensures further investigation and mitigation.
- **Using FTP securely** is critical, as transferring tampered files could introduce risks if not handled properly.
- **Hands-on experience with Linux commands** (like `md5sum` and `openssl`) is valuable for cybersecurity professionals.

## Conclusion

This lab demonstrates how to:

- Use hashing to verify data integrity.
- Detect unauthorized modifications.
- Escalate cybersecurity incidents.
- Implement HMAC for additional security.

These techniques are fundamental for cybersecurity professionals responsible for data integrity and threat mitigation.

---

### Repository Suggestions:

- Include sample hash files (`hashes.txt`).
- Provide example tampered files for testing.
- Add a `README.md` with lab setup instructions.

This lab is an essential exercise for securing sensitive data and ensuring its integrity after cyber incidents. 🚀

---
#### 🔙 [Back To CISCO Labs](/CISCO/Packet-Tracer/)
#### 🔙 [Back To IT Specialist Projects Repository](https://github.com/proxymc/it-specialist-projects)  
