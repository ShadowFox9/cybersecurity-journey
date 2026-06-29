# Week 3 - Nmap Deep Dive & Network Scan

## What I Learned
- How TCP SYN scans work (half-open scan): (1) Nmap sends a 'SYN' packet (pretending to start a connection). (2) if the port is open: target responds 'SYN/ACK', Nmap sends "RST" (reset) thus never completing the handshake but the port has been marked open. (3) if the port is closed: target responds "RST" directly, this means that port is marked closed. (4) If there's no response or icmp error: then the port is filtered.
- Difference between open/closed/filtered ports: Open means that a service is listening and responded. Closed means that port is rechable but no service is listening. Filtered means there's no response at all ( likely a firewall silently dropping the products.
- What NSE scripts do: they do more than the normal nmap scan to check if a port is open. These scripts can detect vulnerabilities, brute-force logins, gather detailed infomation, and even exploit certain weaknesses. therefore they move from is a port open to what is inside the port, is it dangerous.

## Scans I Ran
- Host discovery (-sn): this is a ping scan, i used it to find live devices and to check if the host was alive.
- Service detection (-sV -sC): this detects services versions running on open port (apache 24.41) and also runs defaults safe scripts.
- Full port scan (-p-): this scans all 65535 ports
- Vulnerability scan (-sV --script vuln): this runs all vulnerability detection.

## Key Findings
- My network (192.168.126.0/24) has 4 hosts: - 192.168.126.1 - VMware host machine
  - 192.168.126.2 - DNS server (dnsmasq)
  - 192.168.126.128 - My Kali machine
  - 192.168.126.254 - DHCP/network service
- My Kali machine (.128): 192.168.126.128
- DNS server (.2): 192.168.126.2
- VMware host (.1): 192.168.126.1

## What I Learned Today
i learnt that a scan that shows no result "nothing open" isn't a failed scan but rahther a valuable information. and also that as a  blue teamer that it is important to perfom certain scan on your own machine or what you protect to be able to discover those things a red teamer would discover during recon
