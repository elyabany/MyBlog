ديه Regex هتساعدك انك تعمل maping لل log source 

1. Application="sample-application” 
```
$ name= "(.*?)"\s 
# application="(.*?)"\s
# destination-port="(.*?)"\s
```
2. Application=junos : sample-tcp
```
application=junos:(.*?\s\[\d{1,10}\])
```
3. Application Object ID id=”number”
```
\s+id=(\S+) 
```
4. Authentication Package: ex . NTLM
```
Authentication Package:\s*(\S+)
```
5. Birth Date 
```
((?:0[1-9]|[12]\d|3[01])([\/.-])(?:0[1-9]|1[12])\2(?:(?:19|20)?\d{2}))
```
6. Blocked (yes or no) 
```
"blocked":\s+([a-z]+)
```
7. Bytes & bytes received
```
bytes (\d+)
from-bytes=(\d+)
```
8. Bytes cs-bytes=208 
```
cs-bytes=(\d{1,})
```
9. Capture group example : network DoS attack
```
(.+?)\t(.+)
```
10. CVEID 
```
CVE-(\d*-\d*)
```
11. FInd Command name  
```
CommandName[\=\s]+(.*?)\s*CommandType
```
12. ComponentID
```
Object Name[:\s]+.*?\\CLSID\\\{([\d\w\-]*)\}
```
