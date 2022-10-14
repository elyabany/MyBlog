# Abbreviate a Two Word Name

```python
# Write a function to convert a name into initials. This kata strictly takes two words with one space in between them.

def abbrev_name(name):
     return str(name.split(' ')[0][0]).upper() + "." + str(name.split(' ')[1][0]).upper()
  
```
