# [687. Longest Univalue Path](https://leetcode.com/problems/longest-univalue-path)  
[Ref](https://discuss.leetcode.com/topic/105773/concise-javascript-solution-using-recursion)
## Problem Description
Given a binary tree, find the length of the longest path where each node in the path has the same value. This path may or may not pass through the root.

Note: The length of path between two nodes is represented by the number of edges between them.

Example 1:
```
Input:

              5
             / \
            4   5
           / \   \
          1   1   5
          
Output:
2
```
Example 2:
```
Input:

              1
             / \
            4   5
           / \   \
          4   4   5
          
Output:
2
```
Note: The given binary tree has not more than 10000 nodes. The height of the tree is not more than 1000.

## Solution
This solution is based on understanding the problem definition as follows. The longest Univalue Path falls into ONE of the three possible scenarios:
- It exists somewhere in the Left subtree
- It exists somewhere in the Right subtree
- It exists as a straight path from the Left subtree, through the Root, and to a path in the Right subtree.

Therefore, I needed to write a helper function called straightUnivaluePath, which takes a node and a uniVal, and returns the length of the longest straight path (meaning there is no branching out along the path) through nodes with the uniVal.
```
var straightUnivaluePath = function(node, uniVal) {
    if(!node || node.val !== uniVal) return 0;
    return Math.max(straightUnivaluePath(node.left, uniVal), straightUnivaluePath(node.right, uniVal)) + 1;
}

var longestUnivaluePath = function(root) {
    if(!root) return 0;
    
    return Math.max(
        longestUnivaluePath(root.left),
        longestUnivaluePath(root.right),
        straightUnivaluePath(root.left, root.val) + straightUnivaluePath(root.right, root.val)
    )
};
```

# [110. Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/description/)
[Ref](https://discuss.leetcode.com/topic/7798/the-bottom-up-o-n-solution-would-be-better/19)
## Problem Description
Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

## Solution
This problem is generally believed to have two solutions: the top down approach and the bottom up way.

1. Top-Down : 

  The first method checks whether the tree is balanced strictly according to the definition of balanced binary tree: the difference between the heights of the two sub trees are not bigger than 1, and both the left sub tree and right sub tree are also balanced. With the helper function depth(), we could easily write the code;
  ```
  var height = function(node) {
      if (!node)  return 0;
      return 1 + Math.max(height(node.left), height(node.right));
  }

  var isBalanced = function(root) {
      if (!root)   return true;
      var lh = height(root.left);
      var rh = height(root.right);
      return (Math.abs(lh - rh) <= 1) && isBalanced(root.left) && isBalanced(root.right);
  };
  ```
  For the current node root, calling depth() for its left and right children actually has to access all of its children, thus the complexity is O(N). We do this for each node in the tree, so the overall complexity of isBalanced will be O(N^2). This is a top down approach.

2. Bottom-Up

  The second method is based on DFS. Instead of calling depth() explicitly for each child node, we return the height of the current node in DFS recursion. When the sub tree of the current node (inclusive) is balanced, the function dfsHeight() returns a non-negative value as the height. Otherwise -1 is returned. According to the leftHeight and rightHeight of the two children, the parent node could check if the sub tree is balanced, and decides its return value.
  ```
  var dfsHeight = function(node) {
      if (!node)  return 0;

      var lh = dfsHeight(node.left);
      if (lh === -1)   return -1;

      var rh = dfsHeight(node.right);
      if (rh === -1)   return -1;

      if (Math.abs(lh - rh) > 1)   return -1;
      else     return Math.max(lh, rh) + 1;
  }

  var isBalanced = function(root) {
      return dfsHeight(root) !== -1;
  }
  ```
  In this bottom up approach, each node in the tree only need to be accessed once. Thus the time complexity is O(N), better than the first solution.
