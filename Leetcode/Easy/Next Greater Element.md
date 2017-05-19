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

This solution is just a java version derived from this [post](http://www.geeksforgeeks.org/find-next-greater-number-set-digits/).

At first, lets look at the edge cases -

If all digits sorted in descending order, then output is always “Not Possible”. For example, 4321.
If all digits are sorted in ascending order, then we need to swap last two digits. For example, 1234.
For other cases, we need to process the number from rightmost side (why? because we need to find the smallest of all greater numbers)
Now the main algorithm works in following steps -

I) Traverse the given number from rightmost digit, keep traversing till you find a digit which is smaller than the previously traversed digit. For example, if the input number is “53**4**976”, we stop at **4** because 4 is smaller than next digit 9. If we do not find such a digit, then output is “Not Possible”.

II) Now search the right side of above found digit ‘d’ for the smallest digit greater than ‘d’. For “534**976**″, the right side of 4 contains “976”. The smallest digit greater than 4 is 6.

III) Swap the above found two digits, we get 53**6**97**4** in above example.

IV) Now sort all digits from position next to ‘d’ to the end of number. The number that we get after sorting is the output. For above example, we sort digits in bold 536**974**. We get “536**479**” which is the next greater number for input 534976.

```
var nextGreaterElement = function(n) {
    var arr = n.toString().split('');
    var len = arr.length;
    // I) Start from the right most digit and find the first digit 
    //    that is smaller than the digit next to it.
    var index;
    for (index = len-1; index > 0; index--) {
        if (arr[index-1] < arr[index]) {
            break;
        }
    }
    // If no such digit is found, its the edge case 1.
    if (index === 0) return -1;
    var val = arr[index-1];     // the digit to be changed
    
    // II) Find the smallest digit on right side of (i-1)'th 
    //     digit that is greater than number[i-1]
    var minIdx = index;
    for (var i = index+1; i < len; i++) {
        if (arr[i] > val && arr[i] <= arr[minIdx]) {
            minIdx = i;
        }
    }
    
    // III) Swap the above found smallest digit with number[i-1]
    arr[index-1] = arr[minIdx];
    arr[minIdx] = val;
    // IV) Sort the digits after (i-1) in ascending order
    var rightArr = arr.slice(index).sort(function(a,b) {
        return a-b;
    });
    
    result = Number(arr.slice(0, index).concat(rightArr).join(''));
    return (result < Math.pow(2,31) ? result : -1);   // 32-bit positive integer
    
};
```

