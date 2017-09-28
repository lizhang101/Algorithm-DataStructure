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

### In-place flatten (recursive: bottom->up, right->left)
![recursive flatten](flatten_tree0.jpg)
_**reverse pre-Order**_
```
class Solution {
    private TreeNode prev = null;
    public void flatten(TreeNode root) {
        if(root == null) return;
        flatten(root.right);
        flatten(root.left);
        root.right = prev;
        root.left = null;
        prev = root;
    } 
}
```

# [331. Verify Preorder Serialization of a Binary Tree](https://leetcode.com/problems/verify-preorder-serialization-of-a-binary-tree/description/)

## Description
One way to serialize a binary tree is to use pre-order traversal. When we encounter a non-null node, we record the node's value. If it is a null node, we record using a sentinel value such as #.
```
     _9_
    /   \
   3     2
  / \   / \
 4   1  #  6
/ \ / \   / \
# # # #   # #
```
For example, the above binary tree can be serialized to the string "9,3,4,#,#,1,#,#,2,#,6,#,#", where # represents a null node.

Given a string of comma separated values, verify whether it is a correct preorder traversal serialization of a binary tree. Find an algorithm without reconstructing the tree.

Each comma separated value in the string must be either an integer or a character '#' representing null pointer.

You may assume that the input format is always valid, for example it could never contain two consecutive commas such as "1,,3".

Example 1:
"9,3,4,#,#,1,#,#,2,#,6,#,#"
Return _true_

Example 2:
"1,#"
Return _false_

Example 3:
"9,#,#,1"
Return _false_

## solution
### brute force
Each leaf is represented as "number, #, #". We scan the character array from left to right, and use a stack to maintain characters. When we meet a "#", then check if it's previous character is also a "#", if yes, then pop twice and check again. As long as the prev char is "#", keep pop twice. If not, push one "#", which means we use a null to replace the leaf node. When we done the array traverse, if the stack length is 1 and only contains a "#", return true.
![stack-solution](Preorder-Serialization.jpg)
```
class Solution {
    public boolean isValidSerialization(String preorder) {
        Stack<String>  chars = new Stack();
        for (String c : preorder.split(",")) {
            while (c.equals("#") && !chars.isEmpty() && chars.peek().equals(c)) {
                chars.pop();
                if (chars.isEmpty())    return false;
                chars.pop();
            }
            chars.push(c);
        }
        return chars.size() == 1 && chars.peek().equals("#");
    }
}
```

### indegree and outdegree
In a binary tree, 
- root node provide 0 indegree and 2 outdegree (no parent and 2 children)
- all non-null/non-root node provides 1 indegree and 2 outdegree (1 parent and 2 children)
- all null node provides 1 indegree and 0 outdegree (1 parent and 0 child)

Suppose we try to build this tree. During building, we record the difference between out degree and in degree diff = outdegree - indegree. When the next node comes, we then decrease diff by 1, because the node provides an in degree. If the node is not null, we increase diff by 2, because it provides two out degrees. If a serialization is correct, diff should never be negative and diff will be zero when finished.

Because the first node is root and it has no indegree, so we initialize diff = 1 and after -- the indegree is 0, it's called compensation.

```
class Solution {
    public boolean isValidSerialization(String preorder) {
        int diff = 1;
        for (String node: preorder.split(",")) {
            if (--diff < 0) return false;
            if (!node.equals("#")) diff += 2;
        }
        return diff == 0;
    }
}
```

# [103. Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/)
## Description
Given a binary tree, return the zigzag level order traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).

For example:
Given binary tree [3,9,20,null,null,15,7],
```
    3
   / \
  9  20
    /  \
   15   7
```   
return its zigzag level order traversal as:
```
[
  [3],
  [20,9],
  [15,7]
]
```
## Solution
Learn usage of List of List, add()/add(i).
```
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>>  res = new ArrayList<List<Integer>>();
        traverse(root, 0, res);
        return res;
    }
    private void traverse(TreeNode node, int level, List<List<Integer>> list) {
        if (node == null)   return;
        if (list.size() <= level)    list.add(new LinkedList<Integer>());
        List<Integer>  curList = list.get(level);
        if (level%2 == 0)  {
            curList.add(node.val);
        } else {
            curList.add(0, node.val);
        }
        traverse(node.left, level + 1, list);
        traverse(node.right, level + 1, list);
    }
}
```

# [652. Find Duplicate Subtrees](https://leetcode.com/problems/find-duplicate-subtrees/description/)


# [449. Serialize and Deserialize BST](https://leetcode.com/problems/serialize-and-deserialize-bst/description/)
