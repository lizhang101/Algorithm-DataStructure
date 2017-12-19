# [189. Rotate Array](https://leetcode.com/problems/rotate-array)   
_**try to do this in multiple ways**_
## Problem Description
Rotate an array of n elements to the right by k steps.
```
For example, with n = 7 and k = 3, the array [1,2,3,4,5,6,7] is rotated to [5,6,7,1,2,3,4].
```
Note:

Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.
- Could you do it in-place with O(1) extra space?
- Related problem: [Reverse Words in a String II](https://leetcode.com/problems/reverse-words-in-a-string-ii/)

## Solution
#### Solution 1 : brute force
Remove and insert the last k elements one by one. For example:
`nums = [1,2,3,4,5], k=2`, => `[5,1,2,3,4]` => `[4,5,1,2,3]`.
```
var rotate = function(nums, k) {
    k = k % nums.length;
    while (k > 0) {
        nums.unshift(nums.pop());
        k--;
    }
}
```
#### Solution 2 : 
Remove and insert the last k elements as a chunck. For example:
`nums=[1,2,3,4,5,6,7], k = 3` => `nums=[1,2,3,4], tmp = [5,6,7]` => `nums.unshift(...tmp) = [5,6,7,1,2,3,4]`
OR : `nums = [5,6,7], temp = [1,2,3,4]` => `nums.push(...temp) = [5,6,7,1,2,3,4]`
```
var rotate = function(nums, k) {
    k = k % nums.length;
    nums.unshift(...nums.splice(nums.length-k, k));
    /* or */
    nums.push(...nums.splice(0, nums.length-k));
};
```
#### Solution 3 :
Reverse of reverse. For example:
`nums = [1,2,3,4,5], k=2` => reverse `[1,2,3]` and `[4,5]` inside nums => `[3,2,1,5,4]`, then reverse nums => `[4,5,1,2,3]`.
```
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var rotate = function(nums, k) {
    if (!nums || nums.length < 2)  return;
    k = k % nums.length;    
    reverse(nums, 0, nums.length-k-1);
    reverse(nums, nums.length-k, nums.length-1);
    reverse(nums, 0, nums.length-1);
    
    function reverse(nums, i, j) {
        var tmp;       
        while(i < j){
            tmp = nums[i];
            nums[i] = nums[j];
            nums[j] = tmp;
            i++;
            j--;
        }
    }
};
```
 
# [88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array)
## Problem Description
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

Note:

You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.

## Solution
Because nums1 and nums2 are sorted (ascending) and nums1 has enough space (size >= m+n), so we compare nums1 and nums2 elements from right to left, and always add bigger one to nums1 index from (m+n-1) to 0. And as long as nums2 merged into nums1, the merge is done.
```
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function(nums1, m, nums2, n) {
    var i = m-1, j = n-1, k = m+n-1;
    while (j >= 0) {
        if (i >= 0 && nums1[i] > nums2[j])    nums1[k--] = nums1[i--];
        else                                  nums1[k--] = nums2[j--];
    }
};
```

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

