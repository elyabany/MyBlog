---
description: >-
  Finding subdomains used by the target organization is an effective way to
  increase the attack surface and discover more vulnerabilities.
---

# subdomains Enumeration

1. The script will use a list of potential subdomains and prepends them to the domain name provided via a command-line argument.
2. The script then tries to connect to the subdomains and assumes the ones that accept the connection exist.



```python
import requests      #The requests module allows you to send HTTP requests using Python. 
import sys              # The sys module provides functions and variables which are used to manipulate different parts of the Python Runtime Environment. It lets us access system-specific parameters and functions 

#make a subdomain list and read it 

sub_list = open("subdomains.txt").read() 
subdoms = sub_list.splitlines() 					# The splitlines() method splits a string into a list. The splitting is done at line breaks. 

# Create For loop to take the list of subdomains (subdomains)  and run http request  

for sub in subdoms:
    sub_domains = f"http://{sub}.{sys.argv[1]}" 

    try:
        # requests.get(sub_domains)    	 			#make a GET Request 
          requests.head(sub_domains)          # head Request just like Get Request but without the response body and it make the script faster
    
    except requests.ConnectionError:  			# IF the Request  Failed then Pass 
        pass
    
    else:
        print("Valid domain: ",sub_domains)   
        
```







