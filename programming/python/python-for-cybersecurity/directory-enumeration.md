# Directory Enumeration

```python
import requests 
import sys 

sub_list = open("wordlist.txt").read() 
directories = sub_list.splitlines()

for dir in directories:
    dir_enum = f"http://{sys.argv[1]}/{dir}.html" 
    r = requests.head(dir_enum)
    if r.status_code==404: 
        pass
    else:
        print("Valid directory:" ,dir_enum)
```
