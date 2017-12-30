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
Similar to [746. Min Cost Climbing Stairs](https://leetcode.com/problems/min-cost-climbing-stairs)

# [213. House Robber II](https://leetcode.com/problems/house-robber-ii)
## Problem Description
After robbing those houses on that street, the thief has found himself a new place for his thievery so that he will not get too much attention. This time, all houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, the security system for these houses remain the same as for those in the previous street.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

## Solution
Basic idea : break the circle, the houses you can rob is either house[0 : length-1] or house[1 : length]. base on problem 198.
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var rob = function(nums) {
    if (!nums.length)         return 0;
    if (nums.length === 1)    return nums[0];
    
    return Math.max(helper(nums.slice(0, nums.length-1)), helper(nums.slice(1)));
};

function helper(nums) {
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

# [337. House Robber III](https://leetcode.com/problems/house-robber-iii)
## Problem Description
The thief has found himself a new place for his thievery again. There is only one entrance to this area, called the "root." Besides the root, each house has one and only one parent house. After a tour, the smart thief realized that "all houses in this place forms a binary tree". It will automatically contact the police if two directly-linked houses were broken into on the same night.

Determine the maximum amount of money the thief can rob tonight without alerting the police.

Example 1:
```
     3
    / \
   2   3
    \   \ 
     3   1
Maximum amount of money the thief can rob = 3 + 3 + 1 = 7.
```

Example 2:
```
     3
    / \
   4   5
  / \   \ 
 1   3   1
Maximum amount of money the thief can rob = 4 + 5 = 9.
```

## Solution


