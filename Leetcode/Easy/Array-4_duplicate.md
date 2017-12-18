# [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate)
## Problem Description
Given an array of integers, find if the array contains any duplicates. 
Your function should return true if any value appears at least twice in the array, 
and it should return false if every element is distinct.

## Solution
```
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {  
    var set = new Set();
    for (let n of nums) {
        if (set.has(n))   return true;
        set.add(n);
    }
    return false;
};
```

# [219. Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii)
## Problem Description
Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that `nums[i] = nums[j]` and the absolute difference between i and j is at most k.

## Solution
```
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {boolean}
 */
var containsNearbyDuplicate = function(nums, k) {
    var map = new Map();
    for (var i = 0; i < nums.length; i++) {
        if (map.has(nums[i]) && i-map.get(nums[i]) <= k) {
            return true;
        }
        map.set(nums[i], i);
    }
    return false;
};
```

## Knowledge
- [JavaScript Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)

# [220. Contains Duplicate III](https://leetcode.com/problems/contains-duplicate-iii/description/)  Medium
## Problem Description

## Solution

