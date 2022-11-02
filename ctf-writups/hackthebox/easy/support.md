---
description: windows,Active directory
---

# Support

Start with Nmap scan&#x20;

```bash
# Nmap 7.93 scan initiated Sat Oct 29 18:25:56 2022 as: nmap -A -T4 --open -p- -Pn -v -oN nmap 10.10.11.174
Nmap scan report for 10.10.11.174 (10.10.11.174)
Host is up (0.29s latency).
Not shown: 65515 filtered tcp ports (no-response)
Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
PORT      STATE SERVICE       VERSION
53/tcp    open  domain        Simple DNS Plus
88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2022-10-29 16:35:42Z)
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: support.htb0., Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds?
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp   open  tcpwrapped
3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: support.htb0., Site: Default-First-Site-Name)
3269/tcp  open  tcpwrapped
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
9389/tcp  open  mc-nmf        .NET Message Framing
49664/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49676/tcp open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
49680/tcp open  msrpc         Microsoft Windows RPC
49705/tcp open  msrpc         Microsoft Windows RPC
60598/tcp open  msrpc         Microsoft Windows RPC
60724/tcp open  msrpc         Microsoft Windows RPC
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
OS fingerprint not ideal because: Missing a closed TCP port so results incomplete
No OS matches for host
Uptime guess: 0.850 days (since Fri Oct 28 22:13:32 2022)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=253 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: Host: DC; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
```

Use Crackmapexec For smb port to find the shares

```bash
> crackmapexec smb 10.10.11.174  -u 'a' -p '' --shares                                                                                                                                                            ─╯
SMB         10.10.11.174    445    DC               [*] Windows 10.0 Build 20348 x64 (name:DC) (domain:support.htb) (signing:True) (SMBv1:False)                                                                     
SMB         10.10.11.174    445    DC               [+] support.htb\a:                                                                                                                                               
SMB         10.10.11.174    445    DC               [+] Enumerated shares                                                                                                                                            
SMB         10.10.11.174    445    DC               Share           Permissions     Remark                                                                                                                           
SMB         10.10.11.174    445    DC               -----           -----------     ------                                                                                                                           
SMB         10.10.11.174    445    DC               ADMIN$                          Remote Admin                                                                                                                     
SMB         10.10.11.174    445    DC               C$                              Default share                                                                                                                    
SMB         10.10.11.174    445    DC               IPC$            READ            Remote IPC                                                                                                                       
SMB         10.10.11.174    445    DC               NETLOGON                        Logon server share                                                                                                               
SMB         10.10.11.174    445    DC               support-tools   READ            support staff tools                                                                                                              
SMB         10.10.11.174    445    DC               SYSVOL                          Logon server share                  
```

Use enum4linux&#x20;

```bash

Domain Name: SUPPORT
Domain Sid: S-1-5-21-1677581083-3380853377-188903654

```
