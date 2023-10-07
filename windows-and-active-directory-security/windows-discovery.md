# Windows Discovery

## **Automated Discovery**

***

### **WinPeas**

***

Run WinPeas script for automated discovery

```bash
C:\\\\> winpeas.exe > outputfile.txt
```

### **Windows Exploit Suggester**

***

Update the database

```bash
./windows-exploit-suggester.py --update
```

Analyze the system

```bash
./windows-exploit-suggester.py --database --systeminfo
```

### **Metasploit**

***

Use the Metasploit module for privilege escalatio

```bash
run post/multi/recon/local_exploit_suggester
```

### **WES-NG: Windows Exploit Suggester**

***

Update WES-NG

```bash
wes.py --update
```

Perform system analysis:

```bash
python3 wes.py --update-wes 
python3 wes.py --update wes.py systeminfo.txt
```

### **PowerSploit PowerUp**

***

Use PowerUp checks with Meterpreter

```bash
# OS Info
sysinfo
# Current User
getuid
# Network Information
ifconfig
# Routes
route
# Check ID of the current process 
getpid
# Escalate Privilege
getsystem
# Dump 
Hashes hashdump
```
