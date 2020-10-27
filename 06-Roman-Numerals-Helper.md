# Roman Numerals Helper
## Task
Create a RomanNumerals class that can convert a roman numeral to and from an integer value. It should follow the API demonstrated in the examples below. Multiple roman numeral values will be tested for each helper method.

Modern Roman numerals are written by expressing each digit separately starting with the left most digit and skipping any digit with a value of zero. In Roman numerals 1990 is rendered: 1000=M, 900=CM, 90=XC; resulting in MCMXC. 2008 is written as 2000=MM, 8=VIII; or MMVIII. 1666 uses each Roman symbol in descending order: MDCLXVI.
## Examples

    RomanNumerals.to_roman(1000) # should return 'M'
    RomanNumerals.from_roman('M') # should return 1000

## Help
| Symbol | Value | |----------------| | I | 1 | | V | 5 | | X | 10 | | L | 50 | | C | 100 | | D | 500 | | M | 1000 |

## Solution
```python
class RomanNumerals:
    def init(self):
        pass
    
    def from_roman(roman): 
        values = { 'M': 1000, 'D': 500, 'C': 100, 'L': 50, 'X': 10, 'V': 5, 'I': 1} 
        roman = roman[::-1]
        total=0
        i=0
        while(i<len(roman)):
            if(i!=len(roman)-1):
                if(value[roman[i]]>value[roman[i+1]]):
                    total+=(value[roman[i]]-value[roman[i+1]])
                    i+=1
                else:
                    total+=(value[roman[i]])
            else:
                total+=(value[roman[i]])
            i+=1
        return total
    
    def to_roman(number):
        value_lst = [(1000, 'M'), (900, 'CM'), (500, 'D'), (400, 'CD'), (100, 'C'), (90, 'XC'),
        (50, 'L'), (40, 'XL'), (10, 'X'), (9, 'IX'), (5, 'V'), (4, 'IV'), (1, 'I')]
        roman = ''
        while(number > 0):
            for i, j in value_lst:
                while number >= i:
                    roman += j
                    number -= i
        return roman
    

```
