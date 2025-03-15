# Lab - Configure Authentication and Authorization in Linux

## Objectives
- Add a New Group for Users
- Add Users to the New Group
- Switch Users and Modify Permissions
- Modify Permissions in Absolute Mode

## Overview
In this lab, we use the Linux command line to create a group for new users and add users to the group. Each user is assigned a password for authentication. We then modify permissions to authorize read, write, and execute privileges for users and groups.

## Required Resources
- PC with the CSE-LABVM installed in VirtualBox

## Instructions

### Part 1: Add a New Group for Users

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

### Part 2: Add Users to the New Group

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

#### Step 3: Verify the newly created users in the passwd file
```bash
cat /etc/passwd
```

#### Step 4: View the created users in the shadow file
```bash
cat /etc/shadow
```

### Part 3: Switch Users and Modify Permissions

#### Step 1: Switch user from root to jenny
1. Logout and switch user to Jenny.
2. Open a terminal.

#### Step 2: Explore Jenny's environment
```bash
pwd
cd ../..
ls -l
```

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

### Part 4: Modify Permissions in Absolute Mode

#### Step 1: Switch user from jenny to joe
1. Logout and switch user to Joe.
2. Open a terminal.

Modify permissions using octal values:
```bash
chmod 755 /home/joe
chmod 700 /home/jenny
```

## Lessons Learned
- The `groupadd` and `usermod` commands allow efficient user and group management.
- Permissions (`chmod`) can be set symbolically or with octal values.
- Restricting directory access helps enforce security policies.

## Conclusion
This lab demonstrated the process of configuring authentication and authorization in Linux. By managing users, groups, and permissions, we enforced security principles essential for system administration.
