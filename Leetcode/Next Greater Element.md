## [496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/#/description)
### Problem Description

You are given two arrays (without duplicates) nums1 and nums2 where nums1’s elements are subset of nums2. Find all the next greater numbers for nums1's elements in the corresponding places of nums2.

The Next Greater Number of a number x in nums1 is the first greater number to its right in nums2. If it does not exist, output -1 for this number.

Example 1:
```
Input: nums1 = [4,1,2], nums2 = [1,3,4,2].
Output: [-1,3,-1]
Explanation:
    For number 4 in the first array, you cannot find the next greater number for it in the second array, so output -1.
    For number 1 in the first array, the next greater number for it in the second array is 3.
    For number 2 in the first array, there is no next greater number for it in the second array, so output -1.
```

Example 2:
```
Input: nums1 = [2,4], nums2 = [1,2,3,4].
Output: [3,-1]
Explanation:
    For number 2 in the first array, the next greater number for it in the second array is 3.
    For number 4 in the first array, there is no next greater number for it in the second array, so output -1.
```

Note:
All elements in nums1 and nums2 are unique.
The length of both nums1 and nums2 would not exceed 1000.

### Solutions
#### Solution 1

Brutal method, for each `nums1` element, find it's index in `nums2`, then search right-ward and return the first element which is greater than it; if no greater element exists then return -1.

Code:
  ```
  var nextGreaterElement = function(findNums, nums) {
      var result = [];
      findNums.forEach(function(val) {
          var startIdx = nums.indexOf(val)+1;
          while (startIdx < nums.length) {
              if (nums[startIdx] > val) {
                  result.push(nums[startIdx]);
                  return;
              } else {
                  startIdx++;
              }
          }
          result.push(-1);
      });
      return result;
  };
  ```
  
#### Solution 2

Build a map for each element of `nums2`, key is the element, and value is the element's next greater element.
If an element is not a key of map, means this element doesn't have next greater element.
Use stack and map to implement.

```
var nextGreaterElement = function(findNums, nums) {
    var stack = [];
    var map = [];
    var result = [];
    nums.forEach(function(num) {     // for each element of nums
        while (stack.length > 0 && stack[stack.length-1] < num) {   // num is the next greater element for each element smaller than 
            map[stack.pop()] = num;                                 // it in stack. pop-out and put in map.
        }
        stack.push(num);             // push num in stack for further use
    });
    
    findNums.forEach(function(num) {
        result.push(map[num] || -1);
    });
    
    return result;
}
```

## [503. Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/#/description)


## [556. Next Greater Element III](https://leetcode.com/problems/next-greater-element-iii/#/description)
