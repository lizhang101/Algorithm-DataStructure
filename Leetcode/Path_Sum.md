# [112. Path Sum](https://leetcode.com/problems/path-sum/description/) - E

Given a binary tree and a sum, determine if the tree has a _**root-to-leaf**_ path such that adding up all the values along the path equals the given sum.

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

Solution:
```
class Solution {
    public boolean hasPathSum(TreeNode root, int sum) {
        if (root == null) return false;
        if (root.left == null && root.right == null) return sum == root.val;
        return hasPathSum(root.left, sum - root.val) || hasPathSum(root.right, sum - root.val);
    }  
}
```

# [113. Path Sum II](https://leetcode.com/problems/path-sum-ii/description/) - M

Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.

For example:
Given the below binary tree and sum = 22,
```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
```        
return
```
[
   [5,4,11,2],
   [5,8,4,5]
]
```

Solution: save intermediate result into stack and save the stack into result array once its sum == required sum.
```
class Solution {
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        List<List<Integer>> ans = new ArrayList<List<Integer>>();
        
        helper(ans, new ArrayList<Integer>(), root, sum);
        return ans;
    }
    
    private void helper(List<List<Integer>> ans, List<Integer> path, TreeNode root, int sum) {
        if (root == null) {
            return;
        }
        if (root.left == null && root.right == null) {
            if (sum == root.val) {
                path.add(root.val);
                ans.add(new ArrayList<Integer>(path));
                path.remove(path.size() - 1);
            }
            return;
        }
        
        path.add(root.val);
        helper(ans, path, root.left, sum - root.val);
        helper(ans, path, root.right, sum - root.val);
        path.remove(path.size() - 1);
    }
}
```

# [437. Path Sum III](https://leetcode.com/problems/path-sum-iii/description/) - E

You are given a binary tree in which each node contains an integer value.

Find the number of paths that sum to a given value.

The path does not need to start or end at the root or a leaf, but it must go downwards (traveling only from parent nodes to child nodes).

The tree has no more than 1,000 nodes and the values are in the range -1,000,000 to 1,000,000.

Example:

root = [10,5,-3,3,2,null,11,3,-2,null,1], sum = 8
```
      10
     /  \
    5   -3
   / \    \
  3   2   11
 / \   \
3  -2   1
```
Return 3. The paths that sum to 8 are:
```
1.  5 -> 3
2.  5 -> 2 -> 1
3. -3 -> 11
```

Solution: each time find all the path start from current node, then move start node to the child and repeat.
```
// faster
public class Solution {
    public int pathSum(TreeNode root, int sum) {
        int[] path = new int[1000];
        return findSum(root, sum, path, 0);
    }
    private int findSum(TreeNode root, int sum, int [] path, int level) {
        int result = 0;
        if (root == null)
            return result;
        path[level] = root.val;
        int total=0;
        for (int i=level; i>=0; i--) {
           total+=path[i];
           if (total == sum)
               result++;
        }
       result+=findSum(root.left,sum,path,level+1);
       result+=findSum(root.right,sum,path,level+1);
       return result;
    }
}

// slower
class Solution {
    public int pathSum(TreeNode root, int sum) {
        if (root == null)    return 0;
        return findPath(root, sum) + pathSum(root.left, sum) + pathSum(root.right, sum);
    }
    private int findPath(TreeNode node, int sum) {
        if (node == null)      return 0;
        int res = 0;
        if (node.val == sum)   res++;
        res += findPath(node.left, sum - node.val);
        res += findPath(node.right, sum - node.val);
        return res;
    }
}
```
