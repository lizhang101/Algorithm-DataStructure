## [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)
### Problem Description
Given two strings s and t, write a function to determine if t is an anagram of s.

For example,
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.

Note:
You may assume the string contains only lowercase alphabets.

Follow up:
What if the inputs contain unicode characters? How would you adapt your solution to such case?

### Solution
```
  /**
   * @param {string} s
   * @param {string} t
   * @return {boolean}
   */
  var isAnagram = function(s, t) {
      if (s.length !== t.length)  return false;

      var base = "a".charCodeAt(0);
      var alphs = new Array(26);
      alphs.fill(0);
      for (var i = 0; i < s.length; i++) {
          alphs[s.charCodeAt(i) - base]++;
          alphs[t.charCodeAt(i) - base]--;
      }
      return alphs.every(n => n === 0);
  };
```
## [438. Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/description/)

### Related Questions
- [49. Group Anagrams](https://leetcode.com/problems/group-anagrams/description/)  Medium
