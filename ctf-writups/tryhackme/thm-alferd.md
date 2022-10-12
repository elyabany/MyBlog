# THM : Alferd

&#x20;

&#x20;

[![](https://i.imgur.com/OwWppVP.png)](https://www.blogger.com)&#x20;

### Phases of penetration testing activities include the following:

\
&#x20;   Planning – Customer goals are gathered and rules of engagement obtained.\
&#x20;   Discovery – Perform scanning and enumeration to identify potential vulnerabilities, weak areas, and exploits.\
\
&#x20;   Attack – Confirm potential vulnerabilities through exploitation and perform additional discovery upon new access.\
\
&#x20;   Reporting – Document all found vulnerabilities and exploits, failed attempts, and company strengths and weaknesses.\


![](https://www.blogger.com/img/img-grey-rectangle.png)

\


### scope

| assessment                           | Details       |
| ------------------------------------ | ------------- |
| Internal & external Penetration Test | 10.10.266.244 |

\


### Vulnerability Summary

| Finding             | Severity |
| ------------------- | -------- |
| weak password       | High     |
| RCE                 | High     |
| token impersonation | High     |

\


***

\


starting the pentesting engagement with **Nmap**

```
 sudo nmap -A -T4 --open -vv 10.10.226.224 -oN nmap -Pn
  80/tcp   open  http       syn-ack ttl 127 Microsoft IIS httpd 7.5
|_http-server-header: Microsoft-IIS/7.5
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
|_http-title: Site doesn't have a title (text/html).
3389/tcp open  tcpwrapped syn-ack ttl 127
| ssl-cert: Subject: commonName=alfred
| Issuer: commonName=alfred
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2022-08-11T16:26:23
| Not valid after:  2023-02-10T16:26:23
| MD5:   3038 e053 8bfa 8e35 d8d8 ae42 4a7b c5fc
| SHA-1: c0e0 bea1 b805 d325 2efa 1e3f aa32 23eb 986f 7f57
| -----BEGIN CERTIFICATE-----
| MIIC0DCCAbigAwIBAgIQF06qDRJBJ41Cqf7rqpG8kDANBgkqhkiG9w0BAQUFADAR
| MQ8wDQYDVQQDEwZhbGZyZWQwHhcNMjIwODExMTYyNjIzWhcNMjMwMjEwMTYyNjIz
| WjARMQ8wDQYDVQQDEwZhbGZyZWQwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEK
| AoIBAQDdxRnRn3a5UAn/E89zRhYTH1GyokrqQCp6NgpYYgaa6Y1YCcZnrLGLDEJw
| eXhYOgT1Q/O33soDyDeH9f+Jcp3awG0cG4YGnVh2FEiRwNnwYIVkqJVI0SqtuLYH
| /BKZwU+6LT24xJ8BtFSaORzeQBc3gyfwWkx2RUlGx27VPxqEoLrVKYraw6hyqCE3
| WIJUlMKE7OFpEYPvl1+dRJsCCQki6ZqJrb1uqVNljeFEDc+kZo5kWqd0gnO8jt1I
| dA41BMe4EtIAKmYZGG8IulAotWDhTdXOfSarhoHPVvWTPTXD5uTo0RAcN6sterGO
| WvheMnEL9fm4yGdLUfv8U25U81HvAgMBAAGjJDAiMBMGA1UdJQQMMAoGCCsGAQUF
| BwMBMAsGA1UdDwQEAwIEMDANBgkqhkiG9w0BAQUFAAOCAQEAjjJfpfDBizHwIIDh
| NzHqn1Dz44bnuCkuxdfZ+u3WrqQ0XuflgTMhgbqN8OZZPuXzZHQNdbnYieQimXVw
| kRAR/JbqTC+8s+cYBRytpu/ZSO1f61yz2fiySSxjr/bkrQY/SVr7fpR57BQl6bh9
| Y+lx4ms3p45YcQnuOIPKvIvPw60potiGHWmnT17XWcrA44TFdgB0NITnx7xVNRk2
| AaA/GyIjsbkt/s9fs3kqN8OK3HhkdC3FxPZzRpkW6AsxBwTc5CgeQg7if4CafRSA
| j+G8IXwBpRY5SyTz6YJeSKxEjrF1I9u9RtnnGxOHujkexmOf73s6RTRVP/4ENUT4
| NS4Czg==
|_-----END CERTIFICATE-----
|_ssl-date: 2022-08-12T16:34:20+00:00; 0s from scanner time.
8080/tcp open  http       syn-ack ttl 127 Jetty 9.4.z-SNAPSHOT
|_http-title: Site doesn't have a title (text/html;charset=utf-8).
|_http-favicon: Unknown favicon MD5: 23E8C7BD78E8CD826C5A6073B15068B1
| http-robots.txt: 1 disallowed entry 
|_/
|_http-server-header: Jetty(9.4.z-SNAPSHOT)
   
```

Found 3 port open&#x20;

let's start with port 80 → HTTP\


[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhSbisIVHOoeb2AYUJcvafaAXDGBTL4znAZ2gzGBFvmf\_HZWmyD9pnPHFdW-Trk9I\_DudmWT0Vl\_PNO7NEcCXOKuhyYAfnaGcgo1PEh9HQALZby9Is8l9-mqKebJFinb3LXiKOxcke3hMg9HzrWQRej-IYmy9ejHTwTnlMfsf7IItsQ\_ZjvH9qy9VNf/w638-h335/1.png)](https://www.blogger.com)let's try directory brute forcing[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg3fS7Y5BsiDF1VOIHpCShFaR87Al7VaF2dz3-YLEMJQVMjipFqBkevuY0KQdaRwKWAbEHEVecARFTQG7JpPbUbttFw0GAF8Xy68NmAe\_jVDexC8dgJQv66K0WItMuaccdNJViEMvp3umrp7GmejleD8dTTBzwCGqzdFpi1LBeWOFxdlQHO1tH0PwYx/w517-h278/2.png)](https://www.blogger.com)

we found nothing interesting

***

&#x20;\
Port 8080 → HTTP[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjOT6H\_Cd7-cKiaH9UzGb7YmeGl6QEN1LXKIAmYSC8-l-aLdeW0akC-Gqs9OAV9C0wI2jKZ08hRfXayphjPjRzefYC7Mn4YxMpAHJ-sQtMt4TFF7ziOwEBVBZUPlszmiRd\_NOvSHSQj0Aixw9mD1oT\_yWag0Ipx7fXB0EkwCvpLg0m7hF\_lSYx6bnHb/w435-h331/3.png)](https://www.blogger.com)

&#x20;

&#x20;

&#x20;

&#x20;

&#x20;

&#x20;

&#x20;

&#x20;

&#x20;

***

Try Credential admin:admin, and we get in &#x20;

&#x20;

[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiyu4j4-2bFQoFDGjNkhYhlL4jemPIS91WUwSb8vJ0AOEe3GA2ckN7CI7A42txjU5N5WO6fZqrCFgQwsovI8v-s5lFE-cmXGa\_3R8okFGzIk0SybgVTbP2oJob32OOjtvsT6Rr5ErwynW29SH5aJi4\_76-lOBNiaJ4\_HR0IKAWZpnDpMc1zFA9mIvBd/w640-h256/4.png)](https://www.blogger.com)\


let's look around for something interesting

[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgoNhfJIvAfSUpQmrbyw\_nEBXC3ukOsAkFTW1eF8x6xucoIZWmVhCNYLS6ei3vAN0l7zNga3KHOw6tzDV46Q90RWcWr56jkQba\_WveAbV\_Z4VDxHiHhjwGd5hLS9asvJpiM3k8Kq1xEuMgnS3wmycysZZNVO0goCQ-P1b0NS8W1VTuEMjwJxD6w4hiL/w654-h415/6.png)](https://www.blogger.com)[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEir0Xh2hy4-41jgPd8TM4t53WR3LO8mT35znVsAJofYm8rUWPWzIeM-WW8VE4XYjVvYFWJEU1rm07frQJaFwNIHAB8K4soG6QBj2tXfMv9VYwQIwfUNUciJl8EFLEwUpfmDlKo1mZjrb93IPKuOPt-iG4GNut8Gup8fpp85orQBsnVW2iaLFf5vtmzM/w882-h487/7.png)](https://www.blogger.com)

we can see that there is away we can execute command&#x20;

ok first let's set up a listener with Metasploit&#x20;

[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjNZjObIBGqTfFx0PPeJ4ylMsecdeV2JNwKwmd8S06r2Kdlc06b\_VWH-Zor\_FPDbML2lgW5PPvA0RW4kMey7SGIOx4O4hcdsx8geXEnfQU5SzB7Itp8uX4fUmp41tbg8zhRGDPZPYwndCY2eH7Eo\_Vlm4-H4mwuZvf2cLVmS1vZLV3MzBJWfQ1bQYWZ/s16000/8.png)](https://www.blogger.com)

\
&#x20;now copy the PowerShell command in the command executor&#x20;

&#x20;

[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiGw2x2Y55Nc2Dh1zzvQ3wj3mO\_\_Nv5gK9YF2fBR3pUsgbZ1fEWBtIh71TCP5Kxpi0w6gPS1tCZg-4x8wS8FYSQbEgZvLZc63ZFCDPBkp0tqACsXcHkPIdl93U-cz3UxlvR8dPn\_l9FTLkN6BtOCm2eDKxzJhBHq-0QY9\_6XdjzB12yRsu4yIVkOExr/w779-h279/9.png)](https://www.blogger.com)

\
we got a reverse shell -  sessions to **view the sessions**

[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjTEKWmATqXdb1kvgyWQOlT-rU9jRy4A4Rp76qZT2uGblEOtQ3yRYmRvQ3t2P1mF-bmDbLRSjliKUqqnNV-6-I-mJ36\_NkVQ9RKp0JC9rmvmj1meLpQ9hTQoePGHgP6vmKI4oXqNYmj2Zd9hxoe3TDK9u18dLu7ZCw4wHM85o34Z7AOhS36ylD1OKck/s16000/10.png)](https://www.blogger.com)

Sessions -i → **To interact with the session** &#x20;

**Privilege Escalation:**

Let's use token impersonation to gain system access.&#x20;

1. Load incognito
2. _list\_tokens -g_&#x20;
3. _Impersonate\_token "BUILTIN\Administrators"_\


[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEikWpGj4gwGmieyuPiN-ZSF-wZgN\_egZS6Djr2NfVmdExWMA4hO3aj0Sldqx9ZugTd9GglsvcJq7LZ4uQUnkw6zj70g11RgdyMzMKqd\_R3wMk\_9lp1v4xuqRFVY\_Ygfn83-XvKSDgAxaHu3ICsyKqL0zi-i9JSS2\_67OKnGUfkiGutEsARtSiNd-jlG/s16000/11.png)](https://www.blogger.com)\
[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhSebuA0yFCXF6LFqEhamrujIfR9lwQxzcLHLhoK8SZnEmG2KEZSLGEiF9hXEHPFIPQUd2RKHBTLCT2X65-UzUfVlRITXvvSUaI9BOQmtoOgUkIMK85ItJ32zzJxavTczMEDBV-v9iZYd06qfmsp3\_Lta5MNOaSkfvTv1pFro65\_h6k4soLO1ARjk-c/s16000/12.png)](https://www.blogger.com)

If You cannot find the flag in the default place or there is no hint of the location of the flag, you can use **search command**  to search the system for the file\


[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjo68KrLd2s47HUlNKAxbf2NAhsr16y-MBuyjQrU55V1JKKfD3qs6qQyRi-XRcLyh\_8QEqboy8mJNc-x3cNZQzS7MmgLHGXtTMPftRBPUwLAmQUk29d9Bb2QNfB2uQ5yg2f8B22rXhGdEaLE75pHH-XIJJcMrJm9bG6rqytrIJ48cSFw0Lt56nco-4D/s16000/15.png)](https://www.blogger.com)\
[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiEZ1iWZiwmk07gHB4TLJIUWwy3cZDpkcQWLxkMS6BfdrKXT5zVTNAohLFkhOoxNPxfSc500QQNh7koDk7Wx4USnTBqFoBwPnypQG0zgL50tk5HlVxipLOuILyreE5gZgEZ3wWUZ9Qqt1pjb11H5Zx8jTpeXoF5XFbq4xEKgV2XhuJlscuPcPIXpPdk/s16000/14.png)](https://www.blogger.com)\


\


\


\


\


\


\


\
\
\
