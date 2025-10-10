# -Task-1-Scan-Your-Local-Network-for-Open-Ports

Task 1: Scanning Local Network for Open Ports using Nmap on Kali Linux
## Objective 
- The objective of this Task is to learn how to scan port in local network using Nmap and analysing port in WireShark.
## Tools used 
- **Nmap**: Pre installed in kali linux
- **WireShark**: Pre installed in kali linux
- **Environment**: Kali linux using Vmwar, Virtualnetwork range 192.168.117.0/24, in NAT network Adapter.
## Step 1:
- Running nmap --version to check the tool is installed or not.
- <img width="648" height="154" alt="nmap version" src="https://github.com/user-attachments/assets/39b28511-a754-44f8-af35-7300e49d9bdc" />

## Step 2: Finding Local ip range
- Checking ip address, sudnetmask in Treminal using **ip addr show** command
- 
- <img width="801" height="262" alt="ip Address and class" src="https://github.com/user-attachments/assets/ce697c63-a3fd-47da-96a2-e7f8bbf45d96" />

## Step 3: Running Nmap command 
- Command : Running `nmap -sS 192.168.117.129/24` (TCP SYN scan).

<img width="816" height="84" alt="ip scanning" src="https://github.com/user-attachments/assets/ae698994-dced-478f-887f-4374786d38a9" />

## Step 4: Scan result and storing in txt format 
- Command : Running `nmap -sS 192.168.117.129/24 -oN scan_result.txt`
- Scan completed successfully in 8.51 seconds, detecting 4 hosts up.

  <img width="887" height="519" alt="Nmap scan result" src="https://github.com/user-attachments/assets/dbd4847e-ae50-48e6-af7a-c33a767fda46" />
- Saved as `scan_results.txt` using `-oN` flag.

## Step 5 : Note Down IP Addresses and Open Ports
- **Hosts Up**: 4 (VMware virtual devices).
- **Summary**:
  - **192.168.117.1** (Virtual gateway): All ports filtered (MAC: 00:50:56:C0:00:08).
  - **192.168.117.2** (Possible DNS server): Port 53/tcp open (domain); 999 closed (MAC: 00:50:56:E8:78:9F).
  - **192.168.117.254** (Another gateway): All ports filtered (MAC: 00:50:56:F8:5C:D7).
  - **192.168.117.129** (My Kali VM): All ports closed.

## Step 6 : Analyze with Wireshark
- Captured packets during a rescan.
- Filtered for `tcp.port == 53` – observed SYN-ACK responses confirming port 53 is open on 192.168.117.2.
- This visualized the SYN scan process.
  <img width="1353" height="420" alt="using wire shark to analize the port 58" src="https://github.com/user-attachments/assets/90acb1d9-5c2b-40e4-8909-50cd19b9ce55" />

## Step 7 : Research Common Services
- **Port 53/tcp on 192.168.117.2**: DNS (Domain Name System) service. Used for name resolution. Researched via `nmap -sV 192.168.117.2` (showed VMware DNS) and online resources [(e.g., IANA port list)](https://www.geeksforgeeks.org/computer-networks/50-common-ports-you-should-know/).
- Filtered/closed ports indicate no other services exposed.

## Step 8 : Potential Security Risks
- **Overall Assessment**: Low risk in this isolated virtual network, but educational insights:
  - **Port 53 (DNS)**: Vulnerable to amplification attacks (e.g., DDoS) or poisoning if misconfigured.
    <img width="290" height="108" alt="Screenshot 2025-10-11 002656" src="https://github.com/user-attachments/assets/c482c2c1-756c-4dd1-8b8f-59b801da3f55" />
  - **Filtered Ports (.1 and .254)**: Indicates strong firewall protection, reducing exposure. Risk if rules are overly permissive.
  - **Closed Ports (.129)**: Secure by default on Kali; no unnecessary services. Potential risk if services are enabled without authentication.
  - **General Risks**: In virtual environments, open ports could allow lateral movement between VMs. Recommendations: Use VMware network isolation, regular updates, and monitoring tools like tcpdump.
 
## Step 9 : Save scan results
- Text File : Stored in `scan_result.txt` As shown above.

#### Conclusiom :
This task help us to understand the use of tools like `Nmap` and `WireShark` to scan the network and analysing the states of ports like (open, close).







