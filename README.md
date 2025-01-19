#Ping Sweeper


Key Notes:

Requires Root Permissions:
  
  
  The script uses Scapy, which sends raw packets directly at the network layer.
Raw packet manipulation requires administrative privileges on most systems.
To execute the script, you must run it with root or administrative privileges using a command like:
bash
Copy
Edit
sudo python ping_sweep.py <network> <netmask>
Without root privileges, the script might fail or produce incomplete results.
Accuracy Depends on ICMP Permissions:

Some devices, networks, or firewalls are configured to block or ignore ICMP packets (used for pings).
As a result, devices on such networks may appear "offline" even if they are online.
To improve accuracy in such cases, alternative scanning methods (e.g., TCP SYN or ARP scans) may be required.
Use in Controlled Environments:

Scanning networks without permission is considered illegal or unethical in many jurisdictions.
Always obtain proper authorization before running this script on any network.
Use the script responsibly in controlled environments, such as:
Your own network.
Networks where you have explicit permission (e.g., during a pentest or vulnerability assessment).
