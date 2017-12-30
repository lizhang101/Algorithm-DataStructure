# [198. House Robber](https://leetcode.com/problems/house-robber)
## Problem Description
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

Example:
```
Input : [6,2,3,5,1]
Output: 11
```
## Solution
Basic idea: for i-th house, if you already robbed (i-1)th house, then you can not rob current one; or you can rob current one is you robbed the (i-2)th one. So the money you can get is either the money you accumulated from the (i-1)th house, or the money you accumulated from the (i-2)th house plus the i-th house.
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var rob = function(nums) {
    if (!nums.length)         return 0;
    if (nums.length === 1)    return nums[0];
    
    let money = [];
    money[0] = nums[0];
    money[1] = Math.max(nums[0], nums[1]);
    for (let i = 2; i < nums.length; i++) {
        let m = Math.max(money[0]+nums[i], money[1]);
        money[0] = money[1];
        money[1] = m;
    }
    return money[1];
};
```

# [213. House Robber II](https://leetcode.com/problems/house-robber-ii)
## Problem Description

## Solution



# [337. House Robber III](https://leetcode.com/problems/house-robber-iii)
## Problem Description

## Solution


