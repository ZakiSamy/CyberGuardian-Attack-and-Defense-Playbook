# Attack Preparation

## Attack Preparation

***

Attack preparation and network monitoring are crucial steps in the field of cybersecurity, enabling professionals to assess and secure network vulnerabilities effectively. Below, we provide a comprehensive guide on attack preparation techniques and network monitoring commands to help you bolster your cybersecurity efforts.

**View Network Interface Configuration**

To examine the configuration of network interfaces, use the following command:

```bash
ifconfig && iwconfig && airmon-ng
```

**Turn Network Interface On/Off:**

Activate or deactivate a network interface with the following commands:

```bash
ifconfig wlan0 up 
ifconfig wlan0 down
```

**Restart Network Manager**

Restart the network manager service when needed

```bash
service NetworkManager restart
```

**Check WLAN Regulatory Domain**

Verify the WLAN regulatory domain with

```bash
iw reg get
```

**Set WLAN Regulatory Domain**

Modify the WLAN regulatory domain with a command like

```bash
iw reg set HR
```

**Adjust Wireless Interface Power**

Control the power of a wireless interface:

```bash
iwconfig wlan0 txpower 40
```

## Monitor the Target Network

***

**Set Wireless Interface to Monitoring Mode**

Transform a wireless network interface into monitoring mode with

```bash
airmon-ng start wlan0  
ifconfig wlan0 down && iwconfig wlan0 mode monitor && ifconfig wlan0 up
```

**Set Monitoring Mode on a Specific Channel**

```bash
airmon-ng start wlan0 8  
iwconfig wlan0 channel 8
```

**Disable Services that May Interfere**

```bash
airmon-ng check kill
```

**Return Wireless Interface to Managed Mode**

```bash
airmon-ng stop wlan0mon  
ifconfig wlan0 down && iwconfig wlan0 mode managed && ifconfig wlan0 up
```

**Search for Nearby WiFi Networks**

Discover WiFi networks within your range using

```bash
airodump-ng --wps -w airodump_sweep_results wlan0mon  
wash -a -i wlan0mon
```

**\[Optional] Install Reaver/Wash (on WiFi Pineapple Mark VII)**

```bash
opkg update && opkg install libpcap reaver
```

**\[Optional] Install Reaver/Wash (on WiFi Pineapple Nano)**

```bash
opkg update && opkg install libpcap && opkg -d sd install wash
```

**Monitor a WiFi Network for Capturing Handshakes/Requests**

```bash
airodump-ng wlan0mon --channel 8 -w airodump_essid_results --essid essid --bssid FF:FF:FF:FF
```

Please note that if you specified an output file, be sure to stop 'airodump-ng' after monitoring to prevent excessive storage usage.

## Enumerate Network

***

After gaining access and setting up your tools, you can start scanning and enumerating the network. This may include:

* Scanning for open ports on target devices.
* Identifying active hosts on the network.
* Enumerating services and their versions.
* Gathering information about network topology.
