# [283. Move Zeroes](https://leetcode.com/problems/move-zeroes) 
## Problem Description
Given an array `nums`, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

For example, given `nums = [0, 1, 0, 3, 12]`, after calling your function, nums should be `[1, 3, 12, 0, 0]`.

Note:
You must do this in-place without making a copy of the array.
Minimize the total number of operations.

## Solution
```
// Java
public void moveZeroes(int[] nums) {
    if (nums == null || nums.length == 0) return;        

    int insertPos = 0;
    for (int num: nums) {
        if (num != 0) nums[insertPos++] = num;
    }        

    while (insertPos < nums.length) {
        nums[insertPos++] = 0;
    }
}

// JavaScript
var moveZeroes = function(nums) {
    if (!nums || !nums.length)   return;
    var insertPos = 0;
    for (let num of nums) {
        if (num !== 0)  nums[insertPos++] = num;
    }
    while (insertPos < nums.length)   nums[insertPos++] = 0;
};    
```

# [27. Remove Element](https://leetcode.com/problems/remove-element)
## Problem Description
Given an array and a value, remove all instances of that value in-place and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

Example:
```
Given nums = [3,2,2,3], val = 3,

Your function should return length = 2, with the first two elements of nums being 2.
```
## Solution
- Solution 1 : same idea as 283.
  ```
  /**
   * @param {number[]} nums
   * @param {number} val
   * @return {number}
   */
  var removeElement = function(nums, val) {
      if (!nums || !nums.length)   return;
      var insertPos = 0;
      for (let num of nums) {
          if (num !== val)  nums[insertPos++] = num;
      }
      nums = nums.slice(0, insertPos);
      return insertPos;
  };
  ```
  
- Solution 2 : delete all elements value equals to val
  ```
  /**
   * @param {number[]} nums
   * @param {number} val
   * @return {number}
   */
  var removeElement = function(nums, val) {
      for(var i = nums.length - 1; i >= 0; i--){
          if(nums[i] === val){
              nums.splice(i, 1);
          }
      }
  };
  ```
