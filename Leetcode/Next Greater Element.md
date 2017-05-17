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
### Problem Description

Given a circular array (the next element of the last element is the first element of the array), print the Next Greater Number for every element. The Next Greater Number of a number x is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, output -1 for this number.

Example 1:
```
Input: [1,2,1]
Output: [2,-1,2]
Explanation: The first 1's next greater number is 2; 
The number 2 can't find next greater number; 
The second 1's next greater number needs to search circularly, which is also 2.
```
Note: The length of given array won't exceed 10000.

### Solutions
#### Solution 1

Brutal method, for each element circularly search right-ward and return the first greater element. If no greater element, return -1.
```
var nextGreaterElements = function(nums) {
    var result = [];
    var l = nums.length;
    nums.forEach(function(ele, idx, arr) {
        for (i = 1; i < l; i++) {
            var index = (idx + i)%l;
            if (ele < arr[index]) {
                result.push(arr[index]);
                return;
            }
        }
        result.push(-1);
    })
    return result;
};
```

#### Solution 2

Similar as `496. Next Greater Element I`, use stack. The difference is store index instead of element value.
And search range is from 0 to 2*arr_length.

```
var nextGreaterElements = function(nums) {
    var len = nums.length;
    var result = new Array(len);
    result.fill(-1);
    var stack = [];
    for (i = 0; i < 2*len; i++) {
        var index = i % len;
        while (stack.length > 0 && nums[stack[stack.length-1]] < nums[index]) {
            result[stack.pop()] = nums[index];
        }
        if (i < len) stack.push(i);
    }
    return result;
}
```

## [556. Next Greater Element III](https://leetcode.com/problems/next-greater-element-iii/#/description)
### Problem Description

Given a positive 32-bit integer n, you need to find the smallest 32-bit integer which has exactly the same digits existing in the integer n and is greater in value than n. If no such positive 32-bit integer exists, you need to return -1.

Example 1:
```
Input: 12
Output: 21
```
Example 2:
```
Input: 21
Output: -1
```

### Solution

```
var nextGreaterElement = function(n) {
    var arr = n.toString().split('');
    var len = arr.length;
    var index = null;
    var i;
    var result = [];
    for (i = len-1; i > 0; i--) {
        if (arr[i-1] < arr[i]) {
            index = i-1;
            break;
        }
    }
    if (index === null) return -1;
    var val = arr[index];
    var min = 9;
    var minIdx = null;
    for (i = index+1; i < len; i++) {
        if (arr[i] > val && arr[i] <= min) {
            min = arr[i];
            minIdx = i;
        }
    }
    arr[index] = arr[minIdx];
    arr[minIdx] = val;
    result = Number(arr.slice(0, index+1).concat(arr.slice(index+1).sort(function(a,b) {
        return a-b;
    })).join(''));
    
    return (result > Math.MAX_VALUE ? -1:result);
};
```

