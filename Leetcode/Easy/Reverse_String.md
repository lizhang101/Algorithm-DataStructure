## [344. Reverse String](https://leetcode.com/problems/reverse-string/description/)
### Problem Description
Write a function that takes a string as input and returns the string reversed.

Example:
Given s = "hello", return "olleh".

### Solution
- Solution 1:
```
  /**
   * @param {string} s
   * @return {string}
   */
  var reverseString = function(s) {
      return s.split("").reverse().join("");
  };
```
- Solution 2:
```
  /**
   * @param {string} s
   * @return {string}
   */
  var reverseString = function(s) {
      var arr = []
      var result = ""
      arr = s.split("")
      for(var i=arr.length-1;i>=0;i--) {
          result = result + arr[i]
      }
      return result
  };
```

## [541. Reverse String II](https://leetcode.com/problems/reverse-string-ii/description/)
### Problem Description
Given a string and an integer k, you need to reverse the first k characters for every 2k characters counting from the start of the string. If there are less than k characters left, reverse all of them. If there are less than 2k but greater than or equal to k characters, then reverse the first k characters and left the other as original.
```
Example:
Input: s = "abcdefg", k = 2
Output: "bacdfeg"
```
Restrictions:
- The string consists of lower English letters only.
- Length of the given string and k will in the range [1, 10000]

### Solution

For each 2K substring, reverse the first K substring and keep the second K substring untouched.
```
  /**
   * @param {string} s
   * @param {number} k
   * @return {string}
   */
  var reverseStr = function(s, k) {
    var result = '';
    for(var i = 0; i < s.length; i += 2 * k) {
          var str = rStr(s.substr(i, k)) + s.substr(i + k, k);
          result += str;
    }
      return result
  };

  function rStr(s) {
      var a = '';
      for(var i = s.length - 1; i>= 0; i--) {
          a += s[i];
      }
      return a;
  }
```

## [345. Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/description/)
### Problem Description
Write a function that takes a string as input and reverse only the vowels of a string.

Example 1:
Given s = "hello", return "holle".

Example 2:
Given s = "leetcode", return "leotcede".

Note:
The vowels does not include the letter "y".

### Solution

Dual pointer, one iterate from left to right, the other iterate from right to left. When left and right characters are all vowels, swap them. Then keep searching until left >= right
```
  /**
   * @param {string} s
   * @return {string}
   */
  var reverseVowels = function(s) {
      var chars = s.split("");
      var vowels = {"a":true, "e":true, "i":true, "o":true, "u":true, 
                    "A":true, "E":true, "I":true, "O":true, "U":true};

      var left = 0, right = chars.length-1;
      while (true) {  
          if (left >= right)  break;

          while (left < right && !vowels[chars[left]])    left++;
          while (left < right && !vowels[chars[right]])   right--;

          var rightChar = chars[right];
          chars[right] = chars[left];
          chars[left] = rightChar;
          left++;
          right--;
      }
      return chars.join("");
  };    
```

## JavaScript Knowledge
### [String method slice() vs. substring() vs. substr()](http://www.tothenew.com/blog/javascript-slice-vs-substring-vs-substr/)

  All used to return a new string which is part of the original string.

   method | syntax | argument1 | argument2 | rules 
  ------- | ------ | ----------| --------- | ----------------------------------
  slice() | `str.slice(begin[, end])` | _begin_, required.<br>Zero-based index to begin extraction, inclusive. | _end_, optional.<br>Zero-based index to end the extraction, exclusive.<br>If omitted, extract to end of string. | 1) if begin or end < 0 : begin or end += strLen; <br>2) if begin >= end : return empty string;<br>3) if begin or end > strLen : begin or end = strLen;<br>4) if either argument is NaN, it is treated as if it were 0.
  substring() | `str.substring(Start[, End])` | _Start_, required. inclusive.<br>`[0, strLen]` | _End_, optional, exclusive.<br>`[0, strLen]`<br>if omitted, extract to end of string.| 1) if Start >= End or Start >= strLen : return empty string.<br>2) if begin or end > strLen : begin or end = strLen;<br>3) if either argument is less than 0 or is NaN, it is treated as if it were 0.
  substr() | `str.substr(start[, length])` | _start_, required. inclusive. | _length_, number of characters to extract.<br>if omitted (undefined), extract to end of string. | 1) if start >= strLen : return empty string;<br>2) if length <= 0 or is NaN : return empty string;<br>3) if start < 0 : start += strLen;<br>4) if start is NaN : start = 0;
  
