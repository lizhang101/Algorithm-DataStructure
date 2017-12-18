# [349. Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays)
## Problem Description
Given two arrays, write a function to compute their intersection.
```
Example:
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2].
```
Note:
- Each element in the result must be unique.
- The result can be in any order.


## Solution
```
  var intersection = function(nums1, nums2) {    
    var set1 = new Set(nums1);
    var set2 = new Set(nums2);    
    var res = [...set1].filter(x => set2.has(x));
    return res;
  };
```

## Knowledge
- [JavaScript Set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set)
  ```
  // intersect can be simulated via 
  var intersection = [...set1].filter(x => set2.has(x));

  // difference can be simulated via
  var difference = [...set1].filter(x => !set2.has(x));    
  ```
- [JavaScript array filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

# [350. Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii)
## Problem Description
Given two arrays, write a function to compute their intersection.
```
Example:
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2, 2].
```
Note:
- Each element in the result should appear as many times as it shows in both arrays.
- The result can be in any order.

Follow up:
- What if the given array is already sorted? How would you optimize your algorithm?
- What if nums1's size is small compared to nums2's size? Which algorithm is better?
- What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?

## Solution
```
var intersect = function(nums1, nums2) {
    var hash = {};
    var res = [];
    
    for (var i = 0; i < nums1.length; i++) {
        hash[nums1[i]] = hash[nums1[i]] || 0;
        hash[nums1[i]]++;
    }
    
    for (i = 0; i < nums2.length; i++) {
        if (hash[nums2[i]]) {
            res.push(nums2[i]);
            hash[nums2[i]]--;
        }
    }
    return res;
}
```
