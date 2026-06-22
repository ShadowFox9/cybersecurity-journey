# Day 5 - Wireshark Part 2 + Mini Incident Report

## Filters Used
- tcp.flags.syn == 1: this is a filter i used when i wanted my wireshark to disply only SYN packets or connection attempts 
- http.request: i used this when i wanted to see only http requests 
- Follow TCP Stream: i used this filter when i wanted to see the entire conversation between my device and other devices or server, this is to properly investigate if there is any suspicious 

## Findings

### Finding 1: TCP Handshake
What I observed: i saw ip address 192.168.126.128 repeatedly establishing handshake with a server,there by establishing a valid connection  [SYN,ACK]
Why it matters: This handshake pattern is exactly what attackers exploit in things like SYN flood attacks (a type of DoS attack) — where an attacker sends thousands of SYN requests but never completes the handshake, exhausting the server's resources waiting for responses that never come.this can also be seen in nmap sS command

### Finding 2: OCSP Traffic
What I observed: i observed a behind the scene where my brower did an automatic Secure Sockets Layer cirtificate validity check, The request went to ocsp.starfieldtech.com, which is a legitimate certificate authority company.I observed that it was not encrypted, and this is because it's not sensitive data, it's just a certificate check, not personal information. 
Why it matters: it helps to ensure that a websites SSL is still valid

## Conclusion / Analyst Notes
before now i've read about SYN,SYN ACK & ACK, but i never truly understood how it works but now i can confidently explain the tree way handshake that goes on behind the scene before any connection between devices or devices to server is established.
