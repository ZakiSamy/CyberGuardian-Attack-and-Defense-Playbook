# Nmap

## **What is Nmap?**

Nmap, or Network Mapper, is a powerful open-source tool commonly used for security auditing and network scanning by pentesters. It's designed to discover hosts and services on a computer network and create a map of the network's structure.

* [Nmap Official Website](https://nmap.org/)

## Nmap Cheat Sheet

***

### Basic Nmap Commands

***

**Print Help Screen**

Display the most common command flags and usage information.

```bash
nmap -h
```

**Man Manual Page**

Get detailed information about Nmap commands and usage.

```bash
man nmap
```

### Host Discovery

***

#### **List Scan**

A simple host discovery that lists each host in the specified network(s).

```bash
nmap 192.168.1.1-3 -sL
```

#### **Ping Scan (Ping Sweep)**

Discover hosts by sending ICMP echo requests, TCP SYN to port 443, TCP ACK to port 80, and ICMP timestamp requests.

```bash
nmap 192.168.1.1/24 -sn
```

#### **Disable Host Discovery or Ping Scan**

Perform only a port scan without host discovery.

```bash
nmap 192.168.1.1-5 -Pn
```

#### **ARP Ping Scan**

Utilize ARP packets for host discovery.

```bash
nmap -sn -PR 192.168.1.108
```

#### **Disable ARP Discovery**

Exclude ARP discovery from the scan.

```bash
nmap -sn 192.168.1.108 --disable-arp-ping
```

#### **SCTP INIT Pingscan**

Conduct SCTP INIT ping scans.

```bash
nmap -sn -PY 192.168.1.108 --disable-arp-ping
```

#### Scanning Multiple Targets

Scan multiple hosts simultaneously.

```bash
nmap 192.168.64.135 192.168.64.131
```

#### **Scan IP Range**

Scan hosts in a specified IP range.

```bash
nmap 192.168.64.0/24
```

#### **Scan Host Range**

Scan hosts in a range (e.g., 192.168.64.1 to 192.168.64.254).

```bash
nmap 192.168.64.1-254
```

#### **Scan from File**

Read a list of targets from a file (targets.txt).

```bash
nmap -iL targets.txt
```

#### **Exclude Specific Host**

Exclude a specific host from scanning (e.g., 192.168.64.1).

```bash
nmap 192.168.64.135 --exclude 192.168.64.1
```

#### **Disable DNS Resolution**

Skip DNS resolution for target IP addresses.

```bash
nmap -n 192.168.64.135
```

#### **Enable DNS Resolution**

Force DNS resolution for all target IP addresses.

```bash
nmap -R 192.168.64.135
```

### Port Scanning

***

#### **Default Port Scan**

Perform a port scan on the default 1,000 ports.

```bash
nmap -p 80 192.168.64.135
```

#### **Specify Ports to Scan**

Scan specific ports, e.g., 80 and 22.

```bash
nmap -p 80,22 192.168.64.135
```

#### **Scan Port Range**

Scan ports in a range, e.g., from 1 to 2000.

```bash
nmap -p 1-2000 192.168.64.135
```

#### **Scan All TCP Ports**

Scan all TCP ports on the target.

```bash
nmap -p- 192.168.64.135
```

#### **Scan with Service Names**

Use service names instead of port numbers.

```bash
nmap -p http,https 192.168.64.135
```

#### **Fast Port Scan (Top 100 Ports)**

Quickly scan the top 100 ports.

```bash
nmap -F 192.168.64.135
```

#### **Sequential Port Scan**

Perform a sequential port scan.

```bash
nmap -r 192.168.64.135
```

#### **Specify Number of Top Ports**

Scan the top N ports.

```bash
nmap --top-ports 100 192.168.64.135
```

#### **Exclude Ports from Scanning**

Exclude specific ports from the scan.

```bash
nmap --exclude-ports 80 192.168.64.135
```

#### **TCP SYN Ping Scan**

Use TCP SYN packets for host discovery.

```bash
nmap -sn -PS 192.168.1.108 --disable-arp-ping
```

#### **TCP ACK Ping Scan**

Similar to TCP SYN Ping scan, using TCP ACK packets.

```bash
nmap -sn -PA 192.168.1.108 --disable-arp-ping
```

#### **ICMP Echo Ping Scan**

Use ICMP echo requests to gather information about target systems.

```bash
nmap -sn -PE 192.168.1.108 --disable-arp-ping
```

#### **ICMP ECHO Timestamp Scan**

Perform ICMP ECHO timestamp scans.

```bash
nmap -sn -PP 192.168.1.108 --disable-arp-ping
```

#### **UDP Ping Scan**

Use UDP packets for host discovery.

```bash
nmap -sn -PU 192.168.1.108 --disable-arp-ping
```

### Version Detection

***

#### **Version Detection**

Interrogate ports to determine more about running services.

```bash
nmap -sV 192.168.64.135
```

#### **Version Intensity**

Control the intensity of version detection (0 to 9, default is 7).

```bash
nmap -sV --version-intensity 8 192.168.64.135
```

#### **Version Light Mode**

Enable a faster version scan with reduced accuracy.

```bash
nmap -sV --version-light 192.168.64.135
```

#### **Version All**

Perform an exhaustive version scan.

```bash
nmap -sV --version-all 192.168.64.135
```

#### **Version Trace**

Get detailed debugging info about version scanning.

```bash
nmap -sV --version-trace 192.168.64.135
```

#### **Aggressive Scan**

Enable aggressive scan options including OS detection, version detection, script scanning, and traceroute.

```bash
nmap -A 192.168.64.135
```

### OS Detection

***

#### **OS Detection**

Identify the operating system of the target. Requires sudo privileges.

```bash
sudo nmap -O 192.168.64.135
```

#### **OS Scan Limit**

Limit OS detection to hosts with open and closed ports only.

```bash
sudo nmap -O --osscan-limit 192.168.64.135
```

#### **OS Scan Guess**

Make OS detection more aggressive, providing more guesses.

```bash
sudo nmap -O --osscan-guess 192.168.64.135
```

#### **Maximum OS Detection Tries**

Set the maximum number of OS detection attempts.

```bash
sudo nmap -O --max-os-tries 1 192.168.64.135
```

### Nmap Scripts (NSE)

***

#### **List Nmap Scripts**

View the list of available Nmap scripts.

```bash
ls -l /usr/share/nmap/scripts
```

#### **Script Help**

Get help for a specific Nmap script (e.g., http-enum.nse).

```bash
nmap --script-help http-enum.nse
```

#### **Run Default Nmap Scripts**

Execute the default Nmap script set, useful for discovery and safe scans.

```bash
nmap -sC 192.168.64.135
```

#### **Specify Nmap Scripts**

Run specific Nmap scripts (e.g., http-enum.nse, banner.nse, http-robots.txt.nse).

```bash
nmap --script=http-enum.nse,banner.nse,http-robots.txt.nse 192.168.64.135
```

#### **Run All Scripts (Except Intrusive)**

Execute all scripts except those in the intrusive category.

```bash
nmap --script="not intrusive" 192.168.64.135
```

#### **Script Arguments**

Provide arguments to NSE scripts. Use arguments in a comma-separated list of name=value pairs.

```bash
nmap --script=http-enum.nse --script-args=http-fingerprints.nikto-db-path 192.168.64.135
```

### Timing and Performance

***

#### **Timing Templates**

Control scan timing and performance using timing templates (-T0 to -T5).

```bash
nmap -T4 192.168.64.135
```

#### **Custom Timing Options**

Customize scan timing parameters individually (e.g., --scan-delay, --min-parallelism, --max-parallelism).

```bash
nmap 192.168.64.135 --scan-delay 11s nmap 192.168.64.135 --min-parallelism 2 --max-parallelism 2
```

### Output Formats

***

#### **Save Scan Results**

Save scan results in various formats (e.g., -oN, -oX, -oG).

```bash
nmap -p 80 192.168.64.135 -oN results1
```

#### **Append Scan Results**

Append scan results to an existing file.

```bash
nmap -p 80 192.168.64.135 -oN results1 --append-output
```

#### **XML Output**

Save scan results in XML format (programmatic use).

```bash
nmap -p 80 192.168.64.135 -oX results1.xml
```

#### **Grepable Output**

Save scan results in a grepable format for easy parsing.

```bash
nmap -p 80 192.168.64.135 -oG results2
```

#### **Multiple Output Formats**

Save results in all major formats at once.

```bash
nmap -p 80 192.168.64.135 -oA results3
```

#### **Script Kiddie Output**

Use script kiddie output format for fun and interactivity.

```bash
nmap -p 80 192.168.64.135 -oS results4
```

### Verbosity and Debugging

***

#### **Increase Verbosity**

Increase the verbosity level with -v (1, 2, or 3).

```bash
nmap -v 192.168.64.135
```

#### **Debugging Output**

Enable debugging output (1, 2, or 3) for debugging purposes.

```bash
nmap -d 192.168.64.135
```

#### **Display Port Reasons**

Display reasons for a port's specific state.

```bash
nmap --reason 192.168.64.135
```

#### **Show All Packets Sent and Received**

Display all packets sent and received during the scan. Useful for debugging.

```bash
nmap -T4 --packet-trace 192.168.64.135
```

### Advanced Scanning Techniques

***

#### **Detect Vulnerabilities (e.g., SQL Injection)**

Use Nmap to scan for specific vulnerabilities quickly.

```bash
nmap -sV --script vuln --script-args vulns.showall 192.168.64.135
```

#### **List Supported HTTP Methods**

List supported HTTP methods on a web server.

```bash
nmap -p80 --script http-methods --script-args httpmethods.test-all=true 192.168.64.135
```

#### **Check HTTP Status Codes**

Check the status code response of HTTP methods

```bash
nmap -sV --script http-methods --script-args http-methods.retest 192.168.64.135
```

#### **Enumerate HTTP Information**

Enumerate HTTP-related information on a web server.

```bash
nmap -sV --script http-enum 192.168.64.135
```

#### **Detect Web Application Firewalls (WAF)**

Use Nmap to detect packet filtering systems like WAF or IPS.

```bash
nmap -sV --script http-waf-detect,http-waf-fingerprint 192.168.64.135
```

#### **SQL Injection Scanning**

Quickly scan a web server for SQL injection vulnerabilities.

```bash
nmap -sV --script http-sql-injection 192.168.64.135
```

#### **Find Default Credentials**

Discover default credentials in web services.

```bash
nmap -sV --script http-default-accounts 192.168.64.135
```
