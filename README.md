#Ping Sweeper


Key Notes:

Requires Root Permissions:



This Python script performs a ping sweep to identify live hosts within a specified network range. It leverages the Scapy library for network packet manipulation and the netaddr library for IP address management. The ping_sweep function first calculates all potential host IPs in the specified network by combining the base network address and subnet mask. It iterates through these hosts, sending an ICMP Echo Request (a "ping") to each one using the sr1 function, which waits for a response. If a response is received, the IP address is added to a list of live hosts. Throughout the process, the script tracks and displays scanning progress in real time.



The program takes two command-line arguments: the network address and subnet mask. These inputs define the range of IP addresses to be scanned. After executing the ping_sweep function, it outputs a summary of all hosts that responded to the ping. This tool is useful for network administrators to quickly identify active devices on a network, though it requires administrative privileges to run. It’s important to note that some devices or firewalls may block ICMP requests, which could cause them to appear offline even if they are active.
  


Scanning networks without permission is considered illegal or unethical in many jurisdictions. Always obtain proper authorization before running this script on any network. Use the script responsibly in controlled environments, such as: Your own network. Networks where you have explicit permission (e.g., during a pentest or vulnerability assessment).
