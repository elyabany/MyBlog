# L1: Set Alarm

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

### Solution -> 1&#x20;

```python
def set_alarm(employed, vacation):
    if employed is True and vacation is False:
        return True 
    elif employed is True and vacation is True:
        return False
    elif employed is False and vacation is False:
        return False 
    else:
        return True
```

### Solution -> 2

```python
def set_alarm(employed, vacation):
    return employed and not vacation
```
