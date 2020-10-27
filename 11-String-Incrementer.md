# String incrementer
Your job is to write a function which increments a string, to create a new string.

- If the string already ends with a number, the number should be incremented by 1.
- If the string does not end with a number. the number 1 should be appended to the new string.

## Examples:

    foo -> foo1
    foobar23 -> foobar24
    foo0042 -> foo0043
    foo9 -> foo10
    foo099 -> foo100

Attention: If the number has leading zeros the amount of digits should be considered.

## Solution
```python
def increment_string(strng):
    print(strng)
    new_strng = strng
    s = get_digits(strng)
    s = s[::-1]
    if(not s):
        strng+="1"
    else:         
        strng = strng.replace(s,str(int(s)+1))
        if(len(strng)!=len(new_strng)):
            a = (len(new_strng)-len(strng))*"0"+str(int(s)+1)
            s = get_digits(strng)
            s = s[::-1]
            strng = strng.replace(s,a) 
    return strng

def get_digits(str1):
    str1 = str1[::-1]
    s = ""
    for i in str1:
        if i.isdigit():
            s += i
        else:
            break
    print(s)
    return s
```
