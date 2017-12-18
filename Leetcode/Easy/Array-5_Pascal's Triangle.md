# [118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle)
## Problem Description
Given numRows, generate the first numRows of Pascal's triangle.
```
For example, given numRows = 5,
Return

[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```
## Solution
```
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
    if (!numRows)    return [];
    
    var triangle = [];
    var row = [1];
    for (var i = 0; i < numRows; i++) {
        triangle.push(row);
        row = genRow(row);
    }
    return triangle;
    
    function genRow(arr) {
        var res = [];
        res.push(arr[0]);
        for (var i = 0; i < arr.length-1; i++) {
            res.push(arr[i] + arr[i+1]);
        }
        res.push(arr[arr.length-1]);
        return res;
    }
};
```

# [119. Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii)
## Problem Description
Given an index k, return the kth row of the Pascal's triangle.
```
For example, given k = 3,
Return [1,3,3,1].
```
Note:
Could you optimize your algorithm to use only O(k) extra space?

## Solution
```
/**
 * @param {number} rowIndex
 * @return {number[]}
 */
var getRow = function(rowIndex) {
  let row = [1];
  for (let i = 0; i < rowIndex; i ++) {
    for (let j = 0; j < row.length; j ++) {
      row[j] = row[j] + (row[j + 1] || 0);
    }
    row.unshift(1);
  }
  return row;
};
```
