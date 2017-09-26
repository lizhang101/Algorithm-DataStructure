# [114. Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/description/)

## Description
Given a binary tree, flatten it to a linked list in-place.

For example,
Given
```
         1
        / \
       2   5
      / \   \
     3   4   6
```
The flattened tree should look like:
```
   1
    \
     2
      \
       3
        \
         4
          \
           5
            \
             6
```

## Solution
### brute force
Traverse tree in pre-Order and save nodes to ArrayList sequentially. Then link all the nodes, every node is the right of it's parent node, and every node's left set to null.
```
class Solution {
    ArrayList<TreeNode> nodeList = new ArrayList<TreeNode>();
    public void flatten(TreeNode root) {
        preOrder(root);
        TreeNode node = null;
        for(int i = 0; i < nodeList.size()-1; i++) {
            node = nodeList.get(i);
            node.left = null;
            node.right = nodeList.get(i+1);
        }
    }
    private void preOrder(TreeNode node) {
        if (node == null)   return;
        nodeList.add(node);
        preOrder(node.left);
        preOrder(node.right);
    }
}
```

### recursive flatten (bottom->up, right->left)


