# [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)
## Problem Description
Given a string containing just the characters `'(', ')', '{', '}', '['` and `']'`, determine if the input string is valid.

The brackets must close in the correct order, `"()"` and `"()[]{}"` are all valid but `"(]"` and `"([)]"` are not.

## solution
Basic idea : traverse input string, when met left parenthese, push into stack. when met right parenthese, check if it's pair of the last parenthese. if not, return false. if yes, pop one parenthese. continue.
```
var isValid = function(s) {
    var parenths = {'(':false, ')':'(', '{':false, '}':'{', '[':false, ']':'['};
    var sarr = s.split("");
    var stmp = [];
    for (var i = 0; i < s.length; i++) {
        if (!parenths[sarr[i]])  stmp.push(sarr[i]);
        else {
            if (parenths[sarr[i]] !== stmp[stmp.length-1])    return false;
            stmp.pop();
        }
    }
    return stmp.length === 0;
};
```


# [22. Generate Parentheses](https://leetcode.com/problems/generate-parentheses/description/)  Medium

# [32. Longest Valid Parentheses](https://leetcode.com/problems/longest-valid-parentheses/description/)  Hard

# [301. Remove Invalid Parentheses](https://leetcode.com/problems/remove-invalid-parentheses/description/)  Hard
