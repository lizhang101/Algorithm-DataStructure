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
Basic idea : [ref](https://leetcode.com/problems/house-robber-iii/discuss/79330)

For each node, we can rob it or not rob it. Then we keep track of these two values for each node, e.g. `nodeRes[no_rob, rob]`. So for a node, we also have it's sub-nodes' value : leftRes and rightRes which also have same definition. 
- If we rob current node, then the money we can get should be : `nodeRes[rob] = node.val + leftRes[no_rob] + rightRes[no_rob]`. 
- If we do not rob current node, then the money we can get should be : `nodeRes[no_rob] = Max(leftRes[no_rob], leftRes[rob]) + Max(rightRes[no_rob], rightRes[rob])`. 
- As soon as we reach the root node, max money we can get should be `Max(nodeRes[no_rob], nodeRes[rob])`. 
- If node is null, `nodeRes = [0, 0]`.

```
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */

var rob = function(root) {
    let res = robSub(root);
    return Math.max(res[0], res[1]);
};

function robSub(node) {
    let res = [0, 0];
    if (!node)    return  res;
    
    let left = robSub(node.left);
    let right = robSub(node.right);
    
    res[0] = Math.max(left[0], left[1]) + Math.max(right[0], right[1]);
    res[1] = node.val + left[0] + right[0];
    
    return res;
}
```

