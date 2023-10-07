# Linux Discovery

## **Automated Discovery**

***

### **LinPEAS**

***

Run LinPEAS for comprehensive checks

```bash
# All Checks 
./linpeas.sh -a
# Quick and Stealth Checks 
./linpeas.sh -s
```

## Manual Discovery

***

### OS & System Information Enumeration

***

Check Kernel Version

```bash
uname -a
```

Check Distribution Release Version

```bash
cat /etc/issue 
cat /etc/*release
```

### **User Enumeration**

***

Check user privilege

```bash
id
```

Check the currently logged-in user

```bash
whoami
```

Check the machine's hostname

```bash
hostname
```

List SUDO permissions

```bash
sudo -l
```

Check SUDO version

```bash
sudo -V
```

Check command history

```bash
history cat ~/.bash_history
```

List users on the machine

```bash
ls -l /etc/passwd cat /etc/passwd
```

List password hashes

```bash
ls -l /etc/shadow cat /etc/shadow
```

List groups on the machine

```bash
cat /etc/group
```

### **SSH Key Enumeration**

***

Check for SSH private keys

```bash
find / -name id_rsa 2> /dev/null find / -name authorized_keys 2> /dev/null # In user home directory 
ls -lah ~/.ssh
```

Check for SSH root private key

```bash
# In the Root Directory 
ls -lah /
```

### **File and Permissions Enumeration**

***

Find SUID and SGID files

```bash
find / -type f -perm -04000 -ls 2>/dev/null 
find / -perm /4000 -type f -exec ls -la {} 2>/dev/null 
find / -uid 0 -perm -4000 -type f 2>/dev/null
```

Check Crontab Jobs

```bash
ls -lah /etc/cron* 
cat /etc/crontab
```

List user Crontab jobs:

```bash
crontab -l
```

### **Tools Enumeration**

***

Find common tools

```bash
find / -name perl* -o -name python* -o -name gcc* -o -name nc* -o -name wget* -o -name curl* 2>/dev/null
```

### **Network Configuration and Activities Emueration**

***

Check network configuration

```bash
ifconfig
```

Check network interface configurations

```bash
cat /etc/network/interfaces
```

Check network activity

```bash
netstat -natup ss -natup
```

Check listening ports

```bash
netstat -ano
```

Check DNS configuration

```bash
cat /etc/resolv.conf
```

Check routes

```bash
ip route
```

### **Process and Service Enumeration**

***

List running processes

```bash
ps -ef
```

Check a specific process

```bash
ps -fC PROCESS ps aux | grep PROCESS
```
