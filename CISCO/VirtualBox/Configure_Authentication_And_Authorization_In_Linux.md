# VirtualBox - Configuring Authentication and Authorization in Linux

## 📌Overview
In this lab, I am using the Linux command line to create a group for new users and add users to the group. Each user is assigned a password for authentication. We then modify permissions to authorize read, write, and execute privileges for users and groups.

### Objectives
- Add a New Group for Users
- Add Users to the New Group
- Switch Users and Modify Permissions
- Modify Permissions in Absolute Mode

### [VM Linux Desktop Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/VirtualBox/Images/Configuring%20_Authentication_And_Authorization_In_Linux/VM%20Linux%20Desktop.png)
---
## 🛠Part 1: Add a New Group for Users

#### Step 1: Open a terminal window in the CSE-LABVM
1. Launch the CSE-LABVM.
2. Double-click the Terminal icon to open a terminal.

#### Step 2: Escalate privileges to the root level
```bash
sudo su
```
Enter the password when prompted.

#### Step 3: Add a new group named HR
```bash
groupadd HR
```

#### Step 4: Verify the new group has been added
```bash
cat /etc/group
```
### [Veryfing New Group Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/VirtualBox/Images/Configuring%20_Authentication_And_Authorization_In_Linux/Veryfying%20New%20Group.png)

## 🛠Part 2: Add Users to the New Group

#### Step 1: Add Jenny as a new user and move her to the HR group
```bash
adduser jenny
```
Assign password `jenPass` and fill in user details.

Move Jenny to the HR group:
```bash
usermod -G HR jenny
```

#### Step 2: Add Joe as a new user and move him to the HR group
```bash
adduser joe
```
Assign password `joePass` and fill in user details.

Move Joe to the HR group:
```bash
usermod -G HR joe
```

### [Adding New Users Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/VirtualBox/Images/Configuring%20_Authentication_And_Authorization_In_Linux/Adding%20Users%20To%20HR%20Group.png)

#### Step 3: Verify the newly created users in the passwd file
```bash
cat /etc/passwd
```
### [Veryfing New Users Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/VirtualBox/Images/Configuring%20_Authentication_And_Authorization_In_Linux/Veryfying%20New%20Users.png)

#### Step 4: View the created users in the shadow file
```bash
cat /etc/shadow
```

## 🛠Part 3: Switch Users and Modify Permissions

#### Step 1: Switch user from root to jenny
1. Logout and switch user to Jenny.
2. Open a terminal.

#### Step 2: Explore Jenny's environment
```bash
pwd
cd ../..
ls -l
```
### [Exploring Jennys Environment Image](https://raw.githubusercontent.com/proxymc/it-specialist-projects/refs/heads/main/CISCO/VirtualBox/Images/Configuring%20_Authentication_And_Authorization_In_Linux/Listing%20Users%20Permisions%20on%20Jenny's%20Desktop.png)

Attempt to enter Joe’s directory:
```bash
cd joe
```
Try to create a file:
```bash
touch new.txt
```

#### Step 3: Login as root
```bash
su cisco
sudo -i
```

#### Step 4: Modify the permissions for Joe's home directory
```bash
cd /home
chmod o-x joe
ls -l
```
### [Modyfing Joes Permissions Image](https://github.com/proxymc/it-specialist-projects/blob/main/CISCO/VirtualBox/Images/Configuring%20_Authentication_And_Authorization_In_Linux/Changing%20Joes%20Permissions.png)

#### Step 5: Verify Jenny can no longer access Joe's directory
Logout as root:
```bash
exit
exit
```
Attempt to enter Joe’s directory:
```bash
cd joe
```

## 🛠Part 4: Modify Permissions in Absolute Mode

#### Step 1: Switch user from jenny to joe
1. Logout and switch user to Joe.
2. Open a terminal.

Modify permissions using octal values:
```bash
chmod 755 /home/joe
chmod 700 /home/jenny
```
---
## 📚Lessons Learned
- The `groupadd` and `usermod` commands allow efficient user and group management.
- Permissions (`chmod`) can be set symbolically or with octal values.
- Restricting directory access helps enforce security policies.
---
## Conclusion
This lab demonstrated the process of configuring authentication and authorization in Linux. By managing users, groups, and permissions, we enforced security principles essential for system administration.

---
#### 🔙 [Back To CISCO Labs](/CISCO/VirtualBox/)
#### 🔙 [Back To IT Specialist Projects Repository](https://github.com/proxymc/it-specialist-projects)  
