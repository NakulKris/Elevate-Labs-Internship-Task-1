# Task-1
Scan Your Local Network for Open Ports

1. Objective  
The goal of this task is to perform a TCP SYN port scan on the local network to identify active hosts, discover open ports, and understand basic network exposure.

2. Tools Used  
  1. Nmap  
  2. Wireshark

4. Finding the Local IP Range  
The local IP configuration was checked using:

Command: #ip a 

Result:
- Local device IP:192.168.1.7
- Subnet:/24
- Network range:192.168.1.0/24

This confirmed the correct range for scanning.

4. Nmap Scan Execution  
A TCP SYN scan was performed on the local subnet using:

Command: #nmap -sS 192.168.1.0/24 -oN nmapscan.txt

Explanation:  
-sS  → TCP SYN (stealth) scan  
192.168.1.0/24  → Local network range  
-oN nmapscan.txt  → Save scan output to a text file  

The complete scan output is included in nmapscan.txt in this repository.

5. Scan Results Summary  

Host: 192.168.1.1  
Status: Up  
Open/Filtered Ports:  
53/tcp open  domain  
80/tcp open  http  
5555/tcp filtered  
MAC vendor: Genexis International (router/ONT device)

Host: 192.168.1.7  
Status: Up  
Open Ports:  
1717/tcp open  

Network Summary:  
Total IPs scanned: 256  
Active hosts detected: 2  
Other hosts did not respond or had no open ports.

6. Analysis  

Host: 192.168.1.1  
This is the router or gateway device.  
DNS service running on port 53  
Web interface on port 80  
Port 5555 filtered and likely protected by firewall  
These services are typical for home network routers.

Host: 192.168.1.7  
This is the scanning machine itself.  
One open port detected: 1717/tcp  
A service is listening on this port.

6.1 Port Analysis
  Common Services Running on Detected Ports
  Port 53 (domain): Used for DNS resolution. The router provides DNS services to devices on the network.
  Port 80 (http): Standard web service port. Usually hosts the router’s admin interface.
  Port 5555 (filtered): Often used by remote management or debugging services. The firewall is blocking this port from being scanned.
  Port 1717 (custom/unknown): Not a standard service port. Indicates an application or local service running on the device 192.168.1.7.
  
  Identifying Potential Security Risks
  Port 53: DNS services can be abused for spoofing or poisoning if misconfigured, but risk is low on internal networks when properly secured.
  Port 80: Exposes the router’s web interface. Weak or default credentials could allow full network compromise.
  Port 5555: Although filtered, any remote management service behind this port could be risky if exposed or misconfigured.
  Port 1717: Unknown open ports pose potential risks because the service running on them may be outdated, unnecessary, or vulnerable.


7. Files Included  
nmapscan.txt – Full Nmap scan output  
README.md – This report

8. Outcome  
This task demonstrates basic network reconnaissance, understanding open ports, interpreting Nmap scan results, and identifying potential exposure within a local network.
