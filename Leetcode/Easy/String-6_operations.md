# [67. Add Binary](https://leetcode.com/problems/add-binary/description/)
## Problem Description
Given two binary strings, return their sum (also a binary string).

For example,
```
a = "11"
b = "1"
Return "100".
```

## Solution
If length of input less than max integer, we can use this way:
```
var addBinary = function(a, b) {
    var res = parseInt(a,2) + parseInt(b,2);
    return res.toString(2);
};
```

Most common solution for all posible length of input:
```
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */
var addBinary = function(a, b) {
    var aArr = a.split("");
    var bArr = b.split("");
    var res = "";
    var carry = 0;
    var len = Math.min(aArr.length, bArr.length);
    while (len > 0) {
        var sum = parseInt(aArr.pop()) + parseInt(bArr.pop()) + carry;
        res = sum % 2 + res;
        carry = sum >> 1;
        --len;
    }
    while (aArr.length > 0) {
        var sum = parseInt(aArr.pop()) + carry;
        res = sum % 2 + res;
        carry = sum >> 1;
    }
    while (bArr.length > 0) {
        var sum = parseInt(bArr.pop()) + carry;
        res = sum % 2 + res;
        carry = sum >> 1;
    }
    if (carry > 0)   res = carry + res;
    return res;
};
```
Or 
```
var addBinary = function(a, b) {
    let s = "";
    let c = 0, i = a.length - 1, j = b.length - 1;
    while(i >= 0 || j >= 0 || c == 1) {
        c += i >= 0 ? a[i--] - 0 : 0;
        c += j >= 0 ? b[j--] - 0 : 0;
        s = c%2 + s;
        c = Math.floor(c/2);
    }    
    return s
};
```

# [66. Plus One](https://leetcode.com/problems/plus-one/description/)
## Problem Description
Given a non-negative integer represented as a _**non-empty**_ array of digits, plus one to the integer.

You may assume the integer do not contain any leading zero, except the number 0 itself.

The digits are stored such that the most significant digit is at the head of the list.

## Solution
```
/**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function(digits) {
    var sum = parseInt(digits[digits.length-1]) + 1;
    var carry = Math.floor(sum/10);
    var res = [sum%10];
    for (var i = digits.length-2; i >= 0; i--) {
        sum = parseInt(digits[i]) + carry;
        carry = Math.floor(sum/10);
        res.push(sum % 10);
    }
    if (carry)   res.push(carry);
    return res.reverse();
};
```
Another solution : check if current digit can generate carry, if not, just increase current digit by one and return the whole number. If yes, change it to zero and continue next digit.
```
/**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function(digits) {
    let n = digits.length;
    for (let i = n-1; i >= 0; i--) {
        if (digits[i] < 9) {
            digits[i]++;
            return digits;
        }        
        digits[i] = 0;
    }    
    digits.unshift(1);    
    return digits;
};
```
