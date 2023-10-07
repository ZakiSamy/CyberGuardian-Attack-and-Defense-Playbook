# ffuf

## **Attacking Web Applications with Ffuf**:

### **Web Fuzzing**

```bash
ffuf -w /path/to/web-wordlist.txt -u <http://target.com/FUZZ>
ffuf -w /path/to/wordlist.txt -u <http://target.com/FUZZ>
```

### **Directory Fuzzing**

```bash
ffuf -w /path/to/directory-wordlist.txt -u <http://target.com/FUZZ/>
```

### **Page Fuzzing**

```bash
ffuf -w /path/to/page-wordlist.txt -u <http://target.com/FUZZ.html>
```

### **Recursive Fuzzing**

```bash
ffuf -w /path/to/recursive-wordlist.txt -u <http://target.com/FUZZ/FUZZ>
```

### **DNS Records**

```bash
ffuf -w /path/to/dns-wordlist.txt -u <http://target.com/FUZZ>
```

### **Sub-domain Fuzzing**

```bash
ffuf -w /path/to/subdomain-wordlist.txt -u <http://FUZZ.target.com/>
```

### **Vhost Fuzzing**

```bash
ffuf -w /path/to/vhost-wordlist.txt -H "Host: FUZZ.target.com" -u <http://target.com/>
```

### **Filtering Results**:

```bash
ffuf -w /path/to/wordlist.txt -u <http://target.com/FUZZ> -fc 404
```

### **Parameter Fuzzing - GET**:

```bash
ffuf -w /path/to/param-wordlist.txt -u "<http://target.com/page?param=FUZZ>"
```

### **Parameter Fuzzing - POST**:

```bash
ffuf -w /path/to/param-wordlist.txt -u <http://target.com/login> -X POST -d "username=admin&password=FUZZ"
```

### **Value Fuzzing**

changing a specific parameter's value

```bash
ffuf -w /path/to/value-wordlist.txt -u "<http://target.com/page?param=origina>
```
