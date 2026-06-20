# Phishing Email Analysis - Practice

## Red Flags Identified
- Sense of urgency:  "account locked," "verify within 24 hours or suspended." Attackers create panic so you act fast without thinking carefully. Real banks rarely threaten permanent suspension in 24 hours over email.
- Mismatched domains (From / Reply-To / Return-Path): These are three different domains:

secure-bankalert.com
secure-bankalert-help.com
totally-different-domain.ru

If this was really from my bank, all three should match the bank's real domain. The fact that they're all different is suspicious — it suggests the attacker controls multiple fake domains and is using one to send, another to receive replies, and another to handle bounced emails.
- Fake subdomain trick in link:"  http://secure-bankalert.com.verify-now.ru/login " this link looks like it goes to" secure-bankalert.com"  because that text appears first. But that's not how domains work.
The real domain is always the part right before the first single slash /, reading from left to right but counting dots carefully. The actual website this goes to is " verify-now.ru " a completely random Russian domain. secure-bankalert.com here is just a subdomain trick , it's not the real bank site at all, it's made to look like it by placing it first in the URL. 

## Key Lesson 
it is always important to look deeply into an email especially emails from banks or offical associations that you may not think it'll be fishy,always bear the following questions in :  Who is it claiming to be from? (bank, company, person you know?)
What's the sender's email address exactly?
Does it contain a link? If so, don't click it, as clicking it may expose your device to malware attacks
Does it ask you to do something urgent (reset password, send money, verify account)?
