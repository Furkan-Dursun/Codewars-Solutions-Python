# Last digit of a large number
Define a function that takes in two non-negative integers aaa and bbb and returns the last decimal digit of aba^bab. Note that aaa and bbb may be very large!

For example, the last decimal digit of 979^797 is 999, since 97=47829699^7 = 478296997=4782969. The last decimal digit of (2200)2300({2^{200}})^{2^{300}}(2200)2300, which has over 109210^{92}1092 decimal digits, is 666. Also, please take 000^000 to be 111.

You may assume that the input will always be valid.
## Examples

    last_digit(4, 1)                # returns 4
    last_digit(4, 2)                # returns 6
    last_digit(9, 7)                # returns 9
    last_digit(10, 10 ** 10)        # returns 0
    last_digit(2 ** 200, 2 ** 300)  # returns 6
    
## Solution
```python
cycles = {
    0: [0,0,0,0],   
    1: [1,1,1,1],
    2: [2,4,8,6],
    3: [3,9,7,1],
    4: [4,6,4,6], 
    5: [5,5,5,5], 
    6: [6,6,6,6], 
    7: [7,9,3,1], 
    8: [8,4,2,6], 
    9: [9,1,9,1], 
}

def last_digit(num1, num2):
    if num2 == 0:
        return 1
    else:
        num1_last_digit = int(str(num1)[-1])
        cycle = cycles[num1_last_digit]
        return cycle[(num2 % 4) - 1]
```
