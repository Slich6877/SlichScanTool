# SlichScanTool

This is a scanning tool that I created by combining three well-known tools: Nmap, Gobuster, and Nikto. It provides a simple and efficient way to run multiple security scans for penetration testing.

Installation:

• After downloading the scan tool, grant execute permissions with the following command:

chmod +x pentest_scan.sh

Usage:

• To use the tool, run the following command:

./pentest_scan <TARGET_IP>

Example:

./pentest_scan 10.10.70.211

Features

• This scan tool allows you to run the following scans:

1- Run Nmap scan only
2- Run Gobuster scan only
3- Run Nikto scan only
4- Run Nmap and Gobuster scan only
5- Run Nmap and Nikto scan only
6- Run Gobuster and Nikto scan only
7- Run all three scans (Nmap, Gobuster and Nikto)

Nmap Scan Profiles:

When running the Nmap scan, you will be prompt with the following:

[INFO] Starting Nmap scan for 10.10.70.211...

Choose a scan profile:

1) Fast Open Port Scan
• Description: Fast scan to identify open ports on common services.

2) More Detailed Fast Port Scan (OS, Service) 
• Description: Fast scan with OS detection (-o) and service version detection (-sv) on open ports.

3) Open Port Scan (Full Range, Auth Scripts) 
• Description: Focuses on open ports and performs authentication checks for FTP and SSH services.

4) Comprehensive Service OS Scan (Common Ports) 
• Description: Scans common ports for OS detection, service version detection, and uses default scripts.

5) TCP Connect Scan (Ports 1-1000)
• Description: A TCP connect scan that checks for open ports within the range of 1-1000.

6) UDP Scan (Ports 1-1000)
• Description: Scans UDP ports in the range of 1-1000 with performance optimizations.

7) OS Detection Scan (TCP SYN, Fast)
• Description: Performs a SYN scan for OS detection and open ports in a fast manner.

8) Custom Script Scan (User Defined, Ports 1-1000)
• Description: Allows you to use custom Nmap scripts for your scan on ports 1-1000.

9) Basic Discovery Scan (TCP SYN, Fast)
• Description: Scans a limited set of ports, identifies open ports, and runs discovery scripts.

10) Service Version Scan (Full Range)
Description: Scans all ports (1-65535) for service version detection and open ports.

11) Common Scan (Service, Auth Scripts, OS)
• Description: Performs a scan for common services, OS detection, and authentication scripts like FTP anonymous and SSH brute force.

12) Default Port Scan (TCP SYN)
• Description: A TCP SYN scan that scans all ports and includes service version detection.

13) Vulnerability & Exploit Scan
• Description: Scans for vulnerabilities and exploits across all ports.

14) Standard Scan (Service, Auth Scripts)
• Description: Service version detection, OS detection, and authentication checks using FTP and SSH scripts.

15) Aggressive Scripted Scan (Vuln, Default, OS, Service Version)
• Description: Aggressive scan including OS detection, service version, and vulnerability scripts.
 
16) Comprehensive Scan (Vuln, Aggressive)
• Description: Comprehensive scan that combines vulnerability, discovery, and safe scripts along with service version detection and OS detection.

17) Full Port Scan (Vuln, Aggressive)
• Description: A full port scan (1-65535) with vulnerability detection and discovery scripts.

18) SYN Stealth Scan (Service, Version, OS, Scripts)
• Description: A SYN Stealth scan that performs service version, OS detection, and vulnerability scripts.

19) Firewall Evasion Scan (Decoy, Service, Vuln)
• Description: A scan that evades firewalls by using decoys (need to set the value for the decoys on the variable $DECOY_IP) performs service version detection and vulnerability scanning.

20) Firewall Evasion Scan (Stealth, OS)
• Description: Stealth scan with OS detection and evasion methods.

Scan Completion

• At the end of each Nmap scan, you will receive a desktop notification indicating that the scan has completed successfully for the target IP.

• Results will be stored in a file named nmap_date_timestamp.txt within a newly created directory called logs.

!! Important Scan Profile Color Associations !!

🟢 Green: Fast Scan 

🟡 Yellow: Medium Speed Scan

🔴 Red: Low Speed Scan

🟣 Purple: Stealth Scan

Gobuster Scan

• When running the Gobuster scan, you will be prompted with the following options:

Enter the target URL:

You can use either a website URL or an IP address.

Example: http://10.10.70.211 or http://mywebsite.com

Enter the file extensions to search for:

Provide a comma-separated list of file extensions (e.g., .php,.html,.bak).

Example: .txt,.html,.php,.csv,.xml,.zip,.rar

Choose a wordlist

Choose from the following predefined wordlists:

/usr/share/SecLists/Discovery/Web-Content/common.txt

/usr/share/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt

/usr/share/wordlists/rockyou.txt

!! Important !!

The number of wich wordlist have colors associated:

🟢 Green: Fast Speed

🟡 Yellow: Medium Speed
 
🔴 Red: Low Speed

Gobuster Scan Completion

• At the end of each Gobuster scan, a desktop notification will inform you that the scan completed successfully for the target IP.

• Results will be stored in a file named gobuster_date_timestamp.txt within a newly created logs directory.

• If any status codes between 300-399 (redirection codes) are encountered, the tool will perform recursive scans on those URLs until no further redirections are found.

Recursive Scan Example

• First Gobuster scan finds a status code 301 on http://10.10.70.211/hidden.

• The recursive scan checks http://10.10.70.211/hidden and finds a status code 302 on http://10.10.70.211/hidden/whatever.

• A second recursive scan on http://10.10.70.211/hidden/whatever yields no status codes between 300-399, completing the scan.

• Results for the recursive scan will be stored in gobuster_recursive_date_timestamp.txt.

Nikto Scan

Nikto scans are still in development but include the following profiles:

Simple Scan

• Description: A basic scan for vulnerabilities using multiple test categories.

Default Scan

• Description: A default scan for vulnerabilities.

!! Important !!

The number of wich scan profile have colors associated:

🟢 Green: Simple

🟡 Yellow: Detailed

Nikto Scan Completion

• At the end of each Nikto scan, you will receive a desktop notification indicating the scan has completed.

• Results will be stored in a file named nikto_date_timestamp.html within a newly created logs directory.

Notes:

• The scan tool is designed for use in penetration testing and ethical hacking engagements.

• Always obtain proper authorization before scanning any network or system.
