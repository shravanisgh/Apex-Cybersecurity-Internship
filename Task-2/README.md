Task 2 – Network Scanning, DNS Recon & FTP Packet Analysis

Task 2 focuses on:
* Network scanning with **Nmap**
* Domain information gathering using **WHOIS / DIG / NSLOOKUP**
* FTP login testing on Metasploitable2
* Capturing credentials with **Wireshark**
* Creating basic firewall rules using **iptables**
This task teaches foundational cybersecurity reconnaissance and network traffic analysis.

1. Network Scanning with Nmap
1.1 Host Discovery
Command used:
nmap -sn 192.168.40.0/24
✔ Detected active hosts in the local network
✔ Identified Metasploitable2 and other virtual machines

1.2 Service & Version Scan
Command:
nmap -sV 192.168.40.129
✔ Detected open ports
✔ Retrieved running service versions
✔ Confirmed vulnerable services on Metasploitable2

2. DNS & Domain Reconnaissance
2.1 WHOIS Lookup
Command:
whois google.com
Findings:
* Registrar: MarkMonitor
* DNSSEC enabled
* Domain creation & expiry dates
* Registered name servers

2.2 NSLOOKUP
Command:
nslookup google.com
Observations:
* Returned IPv4/IPv6 addresses
* Confirmed DNS resolution from default name servers

2.3 DIG Query*
Command:
dig google.com
What we obtained:
* Nameserver responses
* A, AAAA records
* Query time & server details

3. FTP Login Testing (Metasploitable2)
3.1 Attempt FTP Login
Commands:
ftp 192.168.40.129
✔ Default login successful: `msfadmin / msfadmin`
✔ Created and tested a new FTP user
✔ Verified insecure plaintext authentication

4. Wireshark Packet Capture (FTP Credentials)
4.1 Captured traffic while logging into FTP
Filtered using:
ftp
tcp.port == 21

4.2 Findings:
* Username and password transferred in plaintext
* Observed packets:
  * `USER shravani`
  * `PASS metas2`
* Confirms FTP is NOT secure (use SSH/SFTP instead)

5. Firewall Testing with iptables
5.1 Blocking Port 22
sudo iptables -A INPUT -p tcp --dport 22 -j DROP
✔ Successfully blocked SSH access
✔ Verified using:
sudo iptables -L

5.2 Removing the rule (optional)
sudo iptables -D INPUT -p tcp --dport 22 -j DROP


Screenshots & Evidence
All screenshots are available in:
Task-2/screenshots/
These include:
* Nmap host scans
* WHOIS, DIG, NSLOOKUP outputs
* FTP login attempts
* Wireshark packet capture
* iptables rule creation


Task 2 Video Walkthrough
Google Drive Video Link:
https://drive.google.com/file/d/1gXRXSPSshrbVvcRkwsreIOaskBo8lqGv/view?usp=drive_link

Task 2 Completed Successfully
This task demonstrated:
* Reconnaissance
* Network discovery
* Service enumeration
* Packet sniffing
* Basic firewall rule creation
