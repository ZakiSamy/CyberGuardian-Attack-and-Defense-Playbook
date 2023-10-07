# Bypass Wireless Protection

## MAC Address Spoofing

***

MAC address spoofing is a technique used to manipulate the Media Access Control (MAC) address of a network interface, typically to bypass MAC address filtering or enhance anonymity. Below are some steps and commands for MAC address spoofing and network enumeration:

### Change MAC Address

If MAC address filtering is active and you need to change the MAC address of a wireless interface to match an existing one, you can use the following commands:

```
# Disable the wireless interface 
ifconfig wlan0 down
# Change the MAC address to FF:FF:FF:FF:FF:FF (replace with the desired MAC)
macchanger --mac FF:FF:FF:FF:FF:FF wlan0
# Enable the wireless interface with the new MAC address
ifconfig wlan0 up`

```

## Post-Access Tools

***

Once you have gained access to a WiFi network, you can run various tools to further explore and assess the network. Here are some examples:

#### Yersinia

***

[Yersinia](https://github.com/tomac/yersinia) is a tool that can be used for various network attacks. To run it:

```
yersinia -G

```

#### Responder

***

[Responder](https://github.com/lgandx/Responder) is a tool for LLMNR, NBT-NS, and MDNS poisoning. To use it for analyzing network traffic

```
responder -wF -I 192.168.8.5

```

#### Wireshark

***

[Wireshark](https://www.wireshark.org/) is a popular network protocol analyzer that allows you to capture and inspect network traffic

```
wireshark

```
