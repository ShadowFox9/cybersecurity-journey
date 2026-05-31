# Day 3 - Linux File System & Navigation

## Key Directories
- /home: where user home directories live, e.g. /home/kali is the kali user's personal folder
- /etc:  system configuration files live here. Very important in security — attackers love this folder
- /var/log: variable data like logs. As a Blue Teamer you'll spend a lot of time in /var/log
- /tmp:  temporary files. Often exploited by attackers to store malicious files because anyone can write here
- /root: the root user's home directory

## Commands Used
- pwd:  shows your current location in the file system
- ls:  lists files and folders in current directory
- cd: change directory
- mkdir:  create a folder
- touch: create an empty file
- cp: copy a file
- mv: move or rename a file
- rm:  delete a file

## What I Learned Today
I explored real directories today, and what stood out to me was the fact a single command can change an entire folder unlike windows where you will have to take certain steps, here a single wrong command can destroy an entire folder also learnt that files such /tmp are not to be treated carelessly as attackers often exploit it, i also learnt why /tmp or /etc matters to me as a future Blue Teamer.
