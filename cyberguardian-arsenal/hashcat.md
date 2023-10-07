# Hashcat

## Hashcat

***

### **Identifying Hashes**

```bash
hashcat -m 0 --example-hashes
```

### **Dictionary Attack**

```bash
hashcat -m [hash_type] -a 0 hashes.txt dictionary.txt
```

### **Combination Attack**

```bash
hashcat -m [hash_type] -a 1 hashes.txt dictionary1.txt dictionary2.txt

```

### **Mask Attack**

```bash
hashcat -m [hash_type] -a 3 hashes.txt ?a?a?a?a?a?a
```

### **Hybrid Mode**

```bash
hashcat -m [hash_type] -a 6 hashes.txt dictionary.txt mask.hcmask
```

### **Working with Rules**

```bash
hashcat -m [hash_type] -a 0 -r rules.rule hashes.txt dictionary.txt
```

### **Cracking Common Hashes**

#### **Cracking NTLM Hashes**

```bash
# Assuming you have a file 'ntlm_hashes.txt' containing NTLM hashes and a dictionary 'dictionary.txt'
hashcat -m 1000 -a 0 ntlm_hashes.txt dictionary.txt
```

#### **Cracking MD5 Hashes**

```bash
# Assuming you have a file 'md5_hashes.txt' containing MD5 hashes and a dictionary 'dictionary.txt'
hashcat -m 0 -a 0 md5_hashes.txt dictionary.txt
```

### **Cracking Miscellaneous Files & Hashes**

#### Cracking a password-protected ZIP

```bash
# Assuming you have a ZIP archive 'protected.zip' and a wordlist 'wordlist.txt'
hashcat -a 0 -m 17200 protected.zip wordlist.txt
```

### **Cracking Wireless (WPA/WPA2) Handshakes with Hashcat**:

```bash
hashcat -m 2500 -a 3 handshake.cap wordlist.txt
```
