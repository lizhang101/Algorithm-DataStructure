# [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)
## Problem Description
Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

For example,
```
"A man, a plan, a canal: Panama" is a palindrome.
"race a car" is not a palindrome.
```
Note:
Have you consider that the string might be empty? This is a good question to ask during an interview.

For the purpose of this problem, we define empty string as valid palindrome.

## Solution
Basic idea is compare all alphanumeric character from left and right to middle, if not equal return false.

You can check alphanumeric character by character when traverse initial string, or remove non-alphanumeric characters at first.

Solution 1:
```
/**
 * @param {string} s
 * @return {boolean}
 */
 var isPalindrome = function(s) {
    s = s.toLowerCase();
    var i = 0, j = s.length-1;
    while (i < j) {
        while (!isAlphanumeric(s.charCodeAt(i)) && i < j)  i++;
        while (!isAlphanumeric(s.charCodeAt(j)) && i < j)  j--;
        if (s.charAt(i) === s.charAt(j))  {i++; j--;}
        else      return false;
    }
    return true;
};

function isAlphanumeric(char_code) {
    return ((char_code > 47 && char_code < 58)   // numeric (0-9)
         || (char_code > 64 && char_code < 91)   // upper alpha (A-Z)
         || (char_code > 96 && char_code < 123)) // lower alpha (a-z));
}
```

Solution 2:
```
var isPalindrome = function(s) {
    s = s.replace(/[^a-zA-Z0-9]/g, "");
    let lo = 0, hi = s.length - 1;    
    while( lo < hi ){
        if (s[lo].toLowerCase() !== s[hi].toLowerCase())   return false;
        lo++; 
        hi--;
    }    
    return true
}
```

## JavaScript
### [RegEx](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp)
- [regex.test V.S. string.match to know if a string matches a regular expression](https://stackoverflow.com/questions/10940137/regex-test-v-s-string-match-to-know-if-a-string-matches-a-regular-expression)
  - `regexObject.test( String )` : Executes the search for a match between a regular expression and a specified string. Returns true or false.    
  - `string.match( RegExp )` : Used to retrieve the matches when matching a string against a regular expression. Returns an array with the matches or null if there are none.
  
- [exec() vs match() vs test() vs search()](https://jsperf.com/exec-vs-match-vs-test-vs-search/2)

### [String.replace()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
The replace() method returns a new string with some or all matches of a pattern replaced by a replacement. The pattern can be a string or a RegExp, and the replacement can be a string or a function to be called for each match.

Note: The original string will remain unchanged.

Syntax : `str.replace(regexp|substr, newSubstr|function)`

### [Best way to alphanumeric check in Javascript](https://stackoverflow.com/questions/4434076/best-way-to-alphanumeric-check-in-javascript)
- [RegEx for Javascript to allow only alphanumeric](https://stackoverflow.com/questions/388996/regex-for-javascript-to-allow-only-alphanumeric/389022#389022)
  ```
  var regex = /^[a-z0-9A-Z]+$/i;
  /*
    ^            start of string
    [a-z0-9A-Z]  a ~ z or 0 ~ 9 or A ~ Z
    +            one or more times (change to * to allow empty string
    $            end of string
    /i           case-insensitive
  */
  regex.test(str);     // return true if str only contains alphanumeric characters.
  ```
  
- check alphanumeric character by character
  ```
  function isAlphanumeric(char_code) {
      return ((char_code > 47 && char_code < 58)   // numeric (0-9)
           || (char_code > 64 && char_code < 91)   // upper alpha (A-Z)
           || (char_code > 96 && char_code < 123)) // lower alpha (a-z));
  }
  ```

# [680. Valid Palindrome II](https://leetcode.com/problems/valid-palindrome-ii/description/)

# [234. Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/description/)
