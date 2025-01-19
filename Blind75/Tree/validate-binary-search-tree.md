# [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)
**Difficulty:** Medium

### Solution in Java
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean isValidBST(TreeNode root) {
        return solve(root, Long.MIN_VALUE, Long.MAX_VALUE); 
    }
    public boolean solve(TreeNode root, long mini, long maxi){
        if(root == null){
            return true;
        }
        if(root.val <= mini || root.val >= maxi){
            return false;
        }
        boolean l = solve(root.left, mini, root.val);
        boolean r = solve(root.right, root.val, maxi);
        return l && r;
    }
}
```
