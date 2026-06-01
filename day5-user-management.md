# Day 5 - Linux User Management

## Why User Management Matters
Controlling who has access to a system is one of the most fundamental security principles. Attackers often target user accounts — creating backdoor accounts, escalating privileges, or hijacking existing ones. As a cybersecurity analyst you need to know how users are managed so you can detect when something is wrong and how to fix it.
## Key Commands
- adduser: Creates a new user with a home directory and prompts for a password.
- passwd:  is used to set or change a user's password on the system.
For example:
When i created testuser, passwd was triggered automatically to set their password
i can also manually change any user's password by running sudo passwd username
A user can change their own password by just running passwd without any username  
- su: Switch to another user account.
- whoami: shows logged in user
- id:  gives more detail — shows user ID (uid), group ID (gid) and all groups the user belongs to.
- usermod: Adding user to a group
- deluser: Deleting a user

## Important Files
- /etc/passwd: stores user account information
- /etc/shadow: stores encrypted passwords. Only root can read this
- /etc/group:  stores group information

## What I Learned Today
i learnt that it is important to understand how to control who has access to a system as it is a fundamental security principle. I created a user, switched to them, accidentally tried to delete the wrong user, traced back and saw my info in /etc/passwd.
