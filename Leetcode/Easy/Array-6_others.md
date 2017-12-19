# [189. Rotate Array](https://leetcode.com/problems/rotate-array)   
_**try to do this in multiple ways**_
## Problem Description

## Solution


# [88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array)
## Problem Description

## Solution


# [645. Set Mismatch](https://leetcode.com/problems/set-mismatch/description/)  
_**three ways**_
## Problem Description
The set S originally contains numbers from 1 to n. But unfortunately, due to the data error, one of the numbers in the set got duplicated to another number in the set, which results in repetition of one number and loss of another number.

Given an array nums representing the data status of this set after the error. Your task is to firstly find the number occurs twice and then find the number that is missing. Return them in the form of an array.
```
Example 1:
Input: nums = [1,2,2,4]
Output: [2,3]
```
Note:
- The given array size will in the range [2, 10000].
- The given array's numbers won't have any order.

## Solution
#### Solution 1 : [put number in postion](https://discuss.leetcode.com/topic/97091/c-6-lines-solution-with-explanation)
The idea is using array indexing, that is putting each `nums[i]` into the position with index `nums[i] - 1`. Then, the array becomes `[1,2,3,4,5...,n]`. So we can find the duplicate number when `nums[i] != i+1`.
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findErrorNums = function(nums) {
    for (var i = 0; i < nums.length; i++) {
        while (nums[i] !== nums[nums[i]-1])   {
            var temp = nums[nums[i]-1];
            nums[nums[i]-1] = nums[i];
            nums[i] = temp;
        }
    }
    for (i = 0; i < nums.length; i++) {
        if (nums[i] !== i+1)   return [nums[i], i+1];
    }
};
```

#### Solution 2 : [using in-position flag](https://discuss.leetcode.com/topic/96808/java-o-n-time-o-1-space)
Base on solution 1's idea, doing swap is time consuming. Using "flag" (negative sign), for each `nums[i]`, we set `nums[nums[i]-1]` to `-1*nums[nums[i]-1]`. If `nums[k]` is duplication, then `nums[nums[k]-1]` is negative beforehand. And after all set, the `nums[m]` which is positive, `m+1` is the missing number.
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findErrorNums = function(nums) {
    var res = [];
    var len = nums.length;
    for (var num of nums) {
        var index = Math.abs(num)-1;
        if (nums[index] < 0)    res.push(Math.abs(num));
        else                    nums[index] *= -1;
    }
    for (i = 0; i < len; i++) {
        if (nums[i] > 0)  {
            res.push(i+1);
            return res;
        }
    }
}
```

#### Solution 3 : [XOR one pass](https://discuss.leetcode.com/topic/96862/xor-one-pass)
Basic idea is : `(1 ^ 2 ^ 3 ^ .. ^ n) ^ (1 ^ 2 ^ 3 ^ .. ^ n) = 0`, Suppose we change 'a' to 'b', then all but 'a' and 'b' are XORed exactly 2 times. The result of XOR is `res = a ^ b`. If we find duplicated number b, then we can get the missing number `a = res ^ b`.
We use the same way of solution 2 to find duplication.
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findErrorNums = function(nums) {
    var res = [0,0];
    var i = 1;
    for (num of nums) {
        num = Math.abs(num);
        
        res[1] ^= i ^ num;
        i++;
        
        if (nums[num-1] < 0)   res[0] = num;
        else                   nums[num-1] *= -1;
    }
    res[1] ^= res[0];
    return res;
}
```

