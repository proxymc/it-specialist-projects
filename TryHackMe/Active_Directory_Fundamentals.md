# Active Directory Fundamentals Lab

## Overview
This lab explores the fundamental functionalities of Active Directory (AD), including organizing Organizational Units (OUs), managing users, delegating permissions, and implementing Group Policy Objects (GPOs). The tasks performed in this lab simulate real-world administrative responsibilities within a corporate environment.

### Objectives
- Organize AD structure by modifying OUs and users.
- Delegate permissions to IT support staff.
- Configure Group Policy Objects (GPOs) for security and management.
- Apply and verify policies using Remote Desktop Protocol (RDP) and PowerShell.

---
### **Part 1: Organizing Active Directory OUs and Users**

#### **Step 1: Reviewing the Existing AD Structure**
- Opened **Active Directory Users and Computers (ADUC)**.
- Enabled `Advanced Features` in the View menu to see hidden properties.
- Identified unnecessary OUs that needed to be removed or modified.

#### **Step 2: Deleting Extra OUs and Users**
- Unchecked `Protect object from accidental deletion` in **Object Properties**.
- Deleted the unnecessary OUs and verified their removal.
- Adjusted user accounts by creating or deleting accounts as per the organizational chart.

---
### **Part 2: Delegating Control to IT Support**

#### **Step 1: Assigning Permissions**
- Opened **ADUC** and navigated to the `Sales` OU.
- Right-clicked the OU and selected **Delegate Control**.
- Added Phillip as a delegate user and assigned him the `Reset user passwords` permission.

#### **Step 2: Verifying Delegation**
- Logged in as Phillip via **RDP** and attempted a password reset:
  ```powershell
  PS C:\Users\phillip> Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose
  PS C:\Users\phillip> Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose
  ```
- Logged in as Sophie to confirm the password reset was required.

---
### **Part 3: Configuring Group Policy Objects (GPOs)**

#### **Step 1: Reviewing Existing GPOs**
- Opened **Group Policy Management**.
- Examined the `Default Domain Policy` and `Default Domain Controllers Policy`.
- Explored password policies under:
  **Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy**.
- Increased the minimum password length policy to 10 characters.

#### **Step 2: Restricting Access to Control Panel**
- Created a new GPO named `Restrict Control Panel Access`.
- Edited **User Configuration → Policies → Administrative Templates → Control Panel → Prohibit Access to Control Panel and PC settings**.
- Linked the GPO to the `Marketing`, `Management`, and `Sales` OUs.

#### **Step 3: Implementing Auto Lock Screen Policy**
- Created a GPO named `Auto Lock Screen`.
- Edited **Computer Configuration → Policies → Windows Settings → Security Settings → Local Policies → Security Options → Interactive Logon: Machine inactivity limit**.
- Set the inactivity timeout to 5 minutes.
- Linked this GPO to the root domain (`thm.local`).

---
### **Part 4: Testing and Verifying Policies**

#### **Step 1: Testing Control Panel Restriction**
- Logged in as `Mark` via RDP:
  ```
  Username: THM\Mark
  Password: M4rk3t1ng.21
  ```
- Attempted to open Control Panel and confirmed access was denied.

#### **Step 2: Testing Auto Lock Screen Policy**
- Waited 5 minutes to verify that the session auto-locked.
- Ran `gpupdate /force` to immediately apply policies.

## Lessons Learned
- **Active Directory Structure**: Organizing OUs correctly ensures streamlined user and device management.
- **Delegation**: Granting specific permissions to IT support improves efficiency without elevating full domain admin rights.
- **Group Policy Management**: GPOs are essential for enforcing security policies and system configurations across departments.
- **Policy Enforcement**: Using `gpupdate /force` ensures that changes are applied immediately.

## Conclusion
This lab provided hands-on experience in managing an enterprise Active Directory environment. By organizing OUs, delegating privileges, and implementing security policies, I gained insight into real-world AD administration tasks. These skills are crucial for maintaining an efficient and secure domain infrastructure.


