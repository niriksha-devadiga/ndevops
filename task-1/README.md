# Task 1: Server Setup and SSH Configuration

> This task demonstrates secure server access using SSH key-based authentication, a fundamental DevOps practice.

---

## Objective
To configure secure server access by setting up a Linux virtual machine and enabling SSH key-based authentication for passwordless login.

---

## Environment Details
- OS: Ubuntu (Virtual Machine)
- Platform: VirtualBox
- User: niriksha

---

## Step 1: Provision Linux Server
A local Ubuntu virtual machine was created using VirtualBox.

---

## Step 2: Install and Configure SSH Server

### Install OpenSSH Server
```bash
sudo apt update
sudo apt install openssh-server -y
```

### Start SSH Service
```bash
sudo systemctl start ssh
```

### Enable SSH on Boot
```bash
sudo systemctl enable ssh
```

### Verify SSH Status
```bash
sudo systemctl status ssh
```

Output shows:
- SSH service is **active (running)**
- Listening on port **22**

---

## Step 3: Get Server IP Address
```bash
ip a
```

IP:
```
127.0.0.1
```

---

## Step 4: Generate SSH Key Pair
```bash
ssh-keygen
```

- Key type: ed25519  
- Private key: `~/.ssh/id_ed25519`  
- Public key: `~/.ssh/id_ed25519.pub`  

---

## Step 5: Configure Passwordless SSH Login

### Copy Public Key to Server
```bash
ssh-copy-id niriksha@127.0.0.1
```

### Connect to Server
```bash
ssh niriksha@127.0.0.1
```

Passwordless login enabled using SSH keys.

---

## Relevant Files
- `~/.ssh/id_ed25519` (Private Key)
- `~/.ssh/id_ed25519.pub` (Public Key)
- `/etc/ssh/sshd_config` (SSH configuration file)

---

## Expected Outcome Achieved
- Linux server successfully provisioned  
- SSH service installed and running  
- SSH key pair generated  
- Passwordless authentication configured  

---

## Conclusion
Secure remote access to the Linux server was successfully established using SSH key-based authentication, eliminating the need for password-based login and improving overall system security.
