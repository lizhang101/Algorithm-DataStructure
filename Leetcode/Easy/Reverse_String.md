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
      var vowels = {"a":true, "e":true, "i":true, "o":true, "u":true, "A":true, "E":true, "I":true, "O":true, "U":true};

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
