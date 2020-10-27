# Regex validate PIN code
ATM machines allow 4 or 6 digit PIN codes and PIN codes cannot contain anything but exactly 4 digits or exactly 6 digits.

If the function is passed a valid PIN string, return `true`, else return `false`.

## Examples
    "1234"   -->  true
    "12345"  -->  false
    "a234"   -->  false
    
## Solution
```python
def validate_pin(pin):
    if(len(pin)==4 or len(pin)==6):
        bool  = True
        for i in range(len(pin)):
            if(pin[i] not in "0123456789"):
                bool  = False
                break
            else:
                bool  = True
        if(bool):
            return True
        else:
            return False
    else:
        return False
```
