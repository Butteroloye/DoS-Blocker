# DoS-Blocker

#import the needed modules 


import sys
from scapy.all import ICMP, IP, sr1
from netaddr import IPNetwork

#ping_sweep Function
def ping_sweep(network, netmask):
live_hosts = []
total_hosts = 0
scanned_hosts = 0


#Calculate Total Hosts
ip_network = IPNetwork(network + '/' + netmask)
for host in ip_network.iter_hosts():
    total_hosts += 1


#Scan Each Host
for host in ip_network.iter_hosts():
    scanned_hosts += 1
    print(f"Scanning: {scanned_hosts}/{total_hosts}", end="\r")


#Ping Each Host
response = sr1(IP(dst=str(host))/ICMP(), timeout=1, verbose=0)


#Check Response
if response is not None:
    live_hosts.append(str(host))
    print(f"Host {host} is online.")


#Return Live Hosts
return live_hosts


#Main Program. This condition ensures that the block of code inside it is only executed when the script is run directly (not imported as a module into another script)
if __name__ == "__main__":
    network = sys.argv[1]
    netmask = sys.argv[2]


#Call ping_sweep
live_hosts = ping_sweep(network, netmask)
print("Completed\n")
print(f"Live hosts: {live_hosts}")


#Run the Script from a CLI using. python ping_sweep.py 192.168.1.0 24

import sys
from scapy.all import ICMP, IP, sr1
from netaddr import IPNetwork

def ping_sweep(network, netmask):
    live_hosts = []
    total_hosts = 0
    scanned_hosts = 0

    ip_network = IPNetwork(network + '/' + netmask)
    for host in ip_network.iter_hosts():
        total_hosts += 1

    for host in ip_network.iter_hosts():
        scanned_hosts += 1
        print(f"Scanning: {scanned_hosts}/{total_hosts}", end="\r")
        response = sr1(IP(dst=str(host))/ICMP(), timeout=1, verbose=0)
        if response is not None:
            live_hosts.append(str(host))
            print(f"Host {host} is online.")

    return live_hosts

if __name__ == "__main__":
    network = sys.argv[1]
    netmask = sys.argv[2]

    live_hosts = ping_sweep(network, netmask)
    print("Completed\n")
    print(f"Live hosts: {live_hosts}")




Key Notes:
Requires Root Permissions:
Scapy sends raw packets, so the script must be run as root.
Use sudo python ping_sweep.py ....
Accuracy Depends on ICMP Permissions:

Some devices or firewalls block ICMP requests, so they might appear offline even if they're online.
Use in Controlled Environments:

Always ensure you have permission to scan a network to avoid legal or ethical issues.
