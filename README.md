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
### Step 2: Finding Local ip range
- Checking ip address, sudnetmask in Treminal using **ip addr show** command
- 
- <img width="801" height="262" alt="ip Address and class" src="https://github.com/user-attachments/assets/ce697c63-a3fd-47da-96a2-e7f8bbf45d96" />

### Step 3: Running Nmap command 
- Command : Running `nmap -sS 192.168.117.129/24` (TCP SYN scan).

<img width="816" height="84" alt="ip scanning" src="https://github.com/user-attachments/assets/ae698994-dced-478f-887f-4374786d38a9" />

### Step 4: Scan result and storing in txt format 
- Command : Running `nmap -sS 192.168.117.129/24 -oN scan_result.txt`
- Scan completed successfully in 8.51 seconds, detecting 4 hosts up.

  <img width="887" height="519" alt="Nmap scan result" src="https://github.com/user-attachments/assets/dbd4847e-ae50-48e6-af7a-c33a767fda46" />

  ### Step 5 :


