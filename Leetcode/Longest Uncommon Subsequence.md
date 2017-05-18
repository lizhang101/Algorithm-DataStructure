## [521. Longest Uncommon Subsequence I](https://leetcode.com/problems/longest-uncommon-subsequence-i/#/description)
### Problem Description
Given a group of two strings, you need to find the longest uncommon subsequence of this group of two strings. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be any subsequence of the other strings.

A **subsequence** is a sequence that can be derived from one sequence by deleting some characters without changing the order of the remaining elements. Trivially, any string is a subsequence of itself and an empty string is a subsequence of any string.

The input will be two strings, and the output needs to be the length of the longest uncommon subsequence. If the longest uncommon subsequence doesn't exist, return -1.

Example 1:
```
Input: "aba", "cdc"
Output: 3
Explanation: The longest uncommon subsequence is "aba" (or "cdc"), 
because "aba" is a subsequence of "aba", 
but not a subsequence of any other strings in the group of two strings. 
```
Note:

Both strings' lengths will not exceed 100.
Only letters from a ~ z will appear in input strings.

### Solution:

For strings A, B, when len(A) > len(B), the longest possible subsequence of either A or B is A, and no subsequence of B can be equal to A. Answer: len(A).

When len(A) == len(B), the only subsequence of B equal to A is B; so as long as A != B, the answer remains len(A).

When A == B, any subsequence of A can be found in B and vice versa, so the answer is -1.

```
var findLUSlength = function(a, b) {
    return a === b ? -1: Math.max(a.length, b.length);
};
```


## [522. Longest Uncommon Subsequence II](https://leetcode.com/problems/longest-uncommon-subsequence-ii/#/description)
### Problem Description
Given a list of strings, you need to find the longest uncommon subsequence among them. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be any subsequence of the other strings.

A **subsequence** is a sequence that can be derived from one sequence by deleting some characters without changing the order of the remaining elements, e.g. `"abc" is subsequence of "aabbcc"`. Trivially, any string is a subsequence of itself and an empty string is a subsequence of any string.

The input will be a list of strings, and the output needs to be the length of the longest uncommon subsequence. If the longest uncommon subsequence doesn't exist, return -1.

Example 1:
```
Input: "aba", "cdc", "eae"
Output: 3
```
Note:

All the given strings' lengths will not exceed 10.
The length of the given list will be in the range of [2, 50].

### Solution:
Traverse the input list of string, find all elements which is not subsequence of all other elements, and return the longest length.
```
var isSubseq = function(str1, str2) {   // return true if str1 is subsequence of str2
    var l = str1.length;
    var n = 0;
    for (var i = 0; i < str2.length; i++) {
        if (n < l && str1[n] == str2[i])   n++;
    }
    return n == l;
} 

var findLUSlength = function(strs) {
    var res = -1;
    for(var i = 0, j; i < strs.length; i += 1) {
        for(j = 0; j < strs.length; j += 1) {
            if(j === i) {
                continue;
            }
            if(isSubseq(strs[i], strs[j])) {
                break;
            }
        }
        if(j === strs.length) {
            res = Math.max(res, strs[i].length);
        }
    }
    return res;
};
```
