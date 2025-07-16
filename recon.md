# Host Discovery & Network Scanning

## Discover live hosts in a subnet
`nmap -sn 192.168.1.0/24`

Scans a subnet to identify which IPs are alive (ping sweep).

## Full TCP port scan with service detection
`nmap -sS -sV -T4 -p- 10.10.10.5`

Stealth TCP scan of all ports with service/version detection.


## OS detection and aggressive scan
`nmap -A 10.10.10.5`

Aggressive scan; OS detection, script scans, traceroute, etc.

## Enumerate UDP ports
`nmap -sU -p- 10.10.10.5`

Enumerates UDP ports, which may expose hidden services.


# DNS & Subdomain Enumeration

## Subdomain brute-forcing
`wfuzz -c -w subdomains.txt -H "Host: FUZZ.example.com" http://example.com`

Brute-forces subdomains using a wordlist and custom Host headers.



## Zone transfer attempt
`dig axfr @ns1.example.com`

Attempts a DNS zone transfer — often misconfigured and exposes all domain records.


## DNS enumeration using dnsenum
`dnsenum --enum -f domains.txt example.com`

Automates DNS enumeration including subdomains, hosts, and NS lookup.


## Find hidden subdomains with Sublist3r
`sublist3r -d example.com`

Scans public sources to find subdomains linked to a target domain.

# Enumeration & Discovery


## SMB share enumeration
`smbclient -L //10.10.10.5 -N`

Lists SMB shares without authentication — can expose sensitive data.


## NetBIOS name and shares
`nmblookup -A 10.10.10.5`

Queries NetBIOS names, often helpful for identifying Windows hostnames and workgroups.


## LDAP enumeration with enum4linux
`enum4linux -a 10.10.10.5`

All-in-one SMB/NetBIOS/LDAP enumeration — a classic for Windows targets.

## Web server enumeration with gobuster
`gobuster dir -u http://10.10.10.5 -w /usr/share/wordlists/dirb/common.txt`

Brute-forces directories and files on a web server — helps reveal hidden content.


# Banner Grabbing & Fingerprinting

## Basic banner grab with Netcat
`nc -vn 10.10.10.5 80`

Connects to port 80 and grabs the service banner — quick fingerprinting.


## HTTP header inspection with Telnet
`telnet 10.10.10.5 80
GET / HTTP/1.1
Host: example.com`

Manual HTTP header inspection via Telnet 


