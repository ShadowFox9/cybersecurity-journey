# Day 4 - Wireshark Basics

## What is Wireshark
Wireshark is a network protocol analyzer that captures and lets you inspect traffic flowing through your network interface in real time.

## Main Panels

- Packet List: shows every packet captured with columns like No., Time, Source, Destination, Protocol, Length, Info
- Packet Details: breaks down the selected packet layer by layer (Ethernet, IP, TCP/UDP, DNS)
- Packet Bytes: shows the raw hex and ASCII view of the packet

## Filters Used
- http: showed 100 packets, all HTTP traffic
- dns: showed 234 packets, including domain lookups like play.google.com and google services
- ip.addr: filtering by my own IP (192.168.126.128) showed only traffic to and from my machine, a mix of DNS queries and TLSv1.3 encrypted application data

## What I Observed During My Capture
I saw DNS queries for play.google.com (both A and AAAA record types), and noticed that even though the actual browsing afterward was encrypted (TLSv1.3), the DNS query itself was not encrypted. In the Packet Bytes panel I could clearly see "play.google.com" in plain readable text in the hex dump.

## What I Learned Today
I learned that DNS queries are not encrypted by default, meaning anyone capturing traffic on the same network could see which websites I'm looking up, even if the rest of my browsing is protected by encryption. This made me realize why DNS spoofing/poisoning is a real risk - if DNS isn't protected, attackers can see or even manipulate where my traffic goes.
