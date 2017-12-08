# [13. Roman to Integer](https://leetcode.com/problems/roman-to-integer/description/)
## Problem Description
Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

## Algorithm
[Algorithm to convert Roman Numerals to Integer Number :](http://www.geeksforgeeks.org/converting-roman-numerals-decimal-lying-1-3999/)
- Split the Roman Numeral string into Roman Symbols (character).
```
{ 'I': 1, 'V': 5, 'X': 10, 'L': 50, 'C': 100, 'D': 500, 'M': 1000 }
```
- Convert each symbol of Roman Numerals into the value it represents.
- Take symbol one by one from starting from index 0:
  - If current value of symbol is greater than or equal to the value of next symbol, then add this value to the running total.
  - else subtract this value by adding the value of next symbol to the running total.

## Solution
```
var romanToInt = function(s) {
    var roman_chars = {'I': 1, 'V': 5, 'X': 10, 'L': 50, 'C': 100, 'D': 500, 'M': 1000};
    var sarr = s.split("").map(c => roman_chars[c]);
    var result = 0;
    for (var i = 0; i < sarr.length-1; i++) {
        if (sarr[i] >= sarr[i+1])   result += sarr[i];
        else    result -= sarr[i];
    }
    result += sarr[sarr.length-1];
    return result;
};
```


[12. Integer to Roman](https://leetcode.com/problems/integer-to-roman/description/)  Medium
8. String to Integer (atoi)
405. Convert a Number to Hexadecimal
