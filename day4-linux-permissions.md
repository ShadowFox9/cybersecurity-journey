# Day 4 - Linux Permissions

## Permission Types
- r (read): can view the file in other words can read the file
- w (write): can modify the file
- x (execute): can run the file as a program 

## Permission Groups
- Owner: the user who created the file 
- Group: this are group of people who make use of the system 
- Others: everyone else on the system  

## Commands Used
- ls -la: lists all files with their details 
- chmod: this is the  command for changing permission
- chown: this is the command for changing ownership
- whoami: this is used to know the user who is logged in

## Numeric Permissions
- 7: rwx(4+2+1)
- 6: rw-(4+2)
- 5: r-x(4+1)
- 4: r--(4)

## What I Learned Today
i learnt that in linux every file and folder has permission that control what one can do with it, this is why it is important to ensure that permissions are configured properly because if they are misconfigured attackers exploit it's vulnerabilities.
