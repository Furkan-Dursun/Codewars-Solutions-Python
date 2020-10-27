# Snail Sort
https://www.codewars.com/kata/521c2db8ddc89b9b7a0000c1

Given an `n x n` array, return the array elements arranged from outermost elements to the middle element, traveling clockwise.

    array = [[1,2,3],
             [4,5,6],
             [7,8,9]]
    snail(array) #=> [1,2,3,6,9,8,7,4,5]
    
For better understanding, please follow the numbers of the next array consecutively:

    array = [[1,2,3],
             [8,9,4],
             [7,6,5]]
    snail(array) #=> [1,2,3,4,5,6,7,8,9]
    
This image will illustrate things more clearly:

![alt text](https://www.haan.lu/files/2513/8347/2456/snail.png)

NOTE: The idea is not sort the elements from the lowest value to the highest; the idea is to traverse the 2-d array in a clockwise snailshell pattern.

NOTE 2: The 0x0 (empty matrix) is represented as en empty array inside an array `[[]]`.

## Solution
```python
def snail(matrix):
    res = []
    if len(matrix) == 0:
        return res
    row_begin = 0
    row_end = len(matrix) - 1
    col_begin = 0
    col_end = len(matrix[0]) - 1

    while row_begin <= row_end and col_begin <= col_end:
        for i in range(col_begin, col_end+1):
            res.append(matrix[row_begin][i])
        row_begin += 1

        for i in range(row_begin, row_end+1):
            res.append(matrix[i][col_end])
        col_end -= 1

        if row_begin <= row_end:
            for i in range(col_end, col_begin-1, -1):
                res.append(matrix[row_end][i])
        row_end -= 1

        if col_begin <= col_end:
            for i in range(row_end, row_begin-1, -1):
                res.append(matrix[i][col_begin])
        col_begin += 1

    return res

```
