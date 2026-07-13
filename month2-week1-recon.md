# Month 2 - Week 1: Ethical Hacking Methodology & Reconnaissance

## The 5 Phases of Ethical Hacking
- Reconnaissance: this is a method used to gather infomations about the target 
- Scanning: a method used to identify open ports,service, and vulnerabilities 
- Exploitation: attempts to exploit discovered vulnerabilities 
- Post-Exploitation: this is where we ask ourselves such questions as, what can i do once inside ? 
- Reporting: this has to do with documenting everything found and how to fix it

## Types of Reconnaissance
- Passive Recon: this means gathering infomations without directly touching the target. this means that the target has no idea that i'm looking at it.
- Active Recon: directly interacting with the target to gather infomation. this means that the target can detect this 

## OSINT Tools Used

### WHOIS
- What it does: this provides such informations as, who owns a domain, when it was registered, contact info
- What I found: detailed infomation about google 

### theHarvester
- What it does: this is a tool that collects emails, subdomains, ip's from public sources
- Command used:i used this command  " theHarvester -d google.com -l 50 -b duckduckgo " 
- What I found: and i found 8 subdomains which are ==== 2Fencrypted.google.com
2Fpatents.google.com
2Fsupport.google.com
Encrypted.google.com
encrypted.google.com
patents.google.com
support.google.com
trends.google.com

### Google Dorking
- What it does: this is using googles own search operators to find things the target didn't intend to expose publicly.
- Dorks I used: 1) site:bbc.com filetype:pdf (2) site:bbc.com inurl:login (3) intitle:"index of" site:bbc.com (4) filetype:env "DB_PASSWORD"
- Most interesting finding: a publicly exposed .env file on GitHub from a real project (open-datenschutzcenter). "db_password@127.0.0.1:5432/db_name..."

## Key Lessons Learned Today
that .env files should never be pushed to GitHub,rather they should always be in .gitignore
This is why tools like GitGuardian exist — they monitor GitHub for accidentally exposed secrets
i also learnt that as a Blue Teamer, i should run Google Dorks against my own organization to find what's accidentally exposed before attackers do
## What I Learned Today
i learnt that as an ethical hacker/blue teamer i should never to exploit what i find. that finding something exposed doesn't give me permission to access it. i should just observe and document what i saw.
