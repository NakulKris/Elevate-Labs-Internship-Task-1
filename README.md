# Task-1
Scan Your Local Network for Open Ports

1. Objective  
The goal of this task is to perform a TCP SYN port scan on the local network to identify active hosts, discover open ports, and understand basic network exposure.

2. Tools Used  
  1. Nmap  
  2. Wireshark

3. Finding the Local IP Range  
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

7. Files Included  
nmapscan.txt – Full Nmap scan output  
README.md – This report

8. Outcome  
This task demonstrates basic network reconnaissance, understanding open ports, interpreting Nmap scan results, and identifying potential exposure within a local network.
