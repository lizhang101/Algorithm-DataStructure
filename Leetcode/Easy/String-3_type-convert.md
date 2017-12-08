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


# [12. Integer to Roman](https://leetcode.com/problems/integer-to-roman/description/)  Medium

# [8. String to Integer (atoi)]()

# [405. Convert a Number to Hexadecimal](https://leetcode.com/problems/convert-a-number-to-hexadecimal/description/)
## Problem Description
Given an integer, write an algorithm to convert it to hexadecimal. For negative integer, two’s complement method is used.

Note:

All letters in hexadecimal (a-f) must be in lowercase.

The hexadecimal string must not contain extra leading 0s. If the number is zero, it is represented by a single zero character '0'; otherwise, the first character in the hexadecimal string will not be the zero character.

The given number is guaranteed to fit within the range of a 32-bit signed integer.

You must not use any method provided by the library which converts/formats the number to hex directly.

Example 1:
```
Input:
26

Output:
"1a"
```

Example 2:
```
Input:
-1

Output:
"ffffffff"
```

## Solution
In JavaScript you can use `number.toString([radix])` to convert a number to a radix-based string. 
- _radix_ is optional, Which base to use for representing a numeric value. Must be an integer between 2 and 36. if omitted radix is 10.
  - 2 : The number will show as a binary value
  - 8 : The number will show as an octal value
  - 16 : The number will show as an hexadecimal value
  
toString does not use two’s complement method to convert negtive number, so you need to handle it by yourself.

Solution:
```
var toHex = function(num) {
    if (num < 0)
    {
        num = 0xffffffff + num + 1;
    }

    return num.toString(16);
};
```
Another solution:
```
var toHex = function(num) {
    var str = ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "a", "b", "c", "d", "e", "f"];
    if (num === 0) return "0";
    var result = "";
    while (num != 0) {
        result = str[num & 0xF] + result;
        num = num >>> 4;
    }
    return result;
};
```
