# Linux  Lateral Movement

### **Custom Port Scanner**

Bash script for custom port scanning

```bash
#!/bin/bash host=192.168.1.1 for port in {1..65535}; do timeout .1 bash -c "echo >/dev/tcp/$host/$port" && echo "Port $port is open" done echo "Done"
```
