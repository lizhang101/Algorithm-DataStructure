# [112. Path Sum](https://leetcode.com/problems/path-sum/description/)  -  Easy
## Problem Description
Given a binary tree and a sum, determine if the tree has a _**root-to-leaf path**_ such that adding up all the values along the path equals the given sum.

For example:
Given the below binary tree and sum = 22,
```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
```        
return true, as there exist a root-to-leaf path 5->4->11->2 which sum is 22.

## Solution
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
 * @param {number} sum
 * @return {boolean}
 */
 var hasPathSum = function(root, sum) {
    var result = false;
    
    function findPath(node, sum) {
        if (!node)   return;
        
        sum -= node.val;
        if (!node.left && !node.right && sum === 0) {
            result = true;
            return;
        }
                
        findPath(node.left, sum);
        findPath(node.right, sum);
    }
    
    findPath(root, sum);
    return result;
};
```

# [437. Path Sum III](https://leetcode.com/problems/path-sum-iii/description/)  -  Easy

# [113. Path Sum II](https://leetcode.com/problems/path-sum-ii/description/)  -  Medium

# [64. Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/description/)   -   Medium

# [129. Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/description/)  -  Medium

# [120. Triangle](https://leetcode.com/problems/triangle/description/)   -   Medium

# [666. Path Sum IV](https://leetcode.com/problems/path-sum-iv)  -  Medium, Locked

# [124. Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/description/)  -  Hard
