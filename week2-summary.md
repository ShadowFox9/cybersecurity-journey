# Week 2 Summary - Networking Basics

## What I Covered
- Day 1-3: Networking fundamentals (TCP/IP, DNS, HTTP/HTTPS, Ports & Protocols) - brushed up from prior knowledge
- Day 4: Wireshark Basics - capturing traffic, filters, packet panels
- Day 5: Wireshark Part 2 + Mini Incident Report - TCP handshake analysis, OCSP traffic investigation

## Skills Gained
I can now open and use Wireshark to capture live packets and network traffic. I also properly understood how the TCP three way handshake works in practice, unlike the theoretical knowledge I had before. I can isolate traffic by applying filters, since a typical Wireshark capture displays numerous different types of traffic like HTTP, DNS, and OCSP. I can now use Follow TCP Stream to reconstruct and read a full conversation between two devices or a server. I also learned to read and understand OCSP checks, and not assume unencrypted traffic is automatically suspicious without understanding why it's unencrypted.
## Tools Used
Kali Linux, Wireshark, nano, git, GitHub
## Biggest Takeaway From The Week
This week moved me from only knowing networking concepts in theory, to being able to confidently use wireshark to capture live traffic, analyze them based on their types using filters and using follow tcp stream to understand what's going on behind the scenes.
The moment that stood out most was seeing the handshake happen live, realizing OCSP wasn't a threat, and seeing how easy using filters can make your work as a cybersecurity analyst.
It made me realize that there's more that goes on behind the scenes when you search for 'orange' on Google or Firefox, apart from just the orange you see on your screen.
I'm proud that I got to properly understand the true importance of Wireshark, apart from just the way it was taught in class
