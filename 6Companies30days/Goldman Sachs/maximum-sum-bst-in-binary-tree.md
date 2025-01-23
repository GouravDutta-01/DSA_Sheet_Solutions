# [Maximum Sum BST in Binary Tree](https://leetcode.com/problems/maximum-sum-bst-in-binary-tree/)
**Difficulty:** Hard

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
    public int maxSumBST(TreeNode root) {
        int[] maxSum = new int[1];
        solve(root, maxSum);  
        return maxSum[0]; 
    }
    public int[] solve(TreeNode root, int[] maxSum){
        if(root == null){
            return new int[]{Integer.MAX_VALUE, Integer.MIN_VALUE, 0};
        }
        int[] left = solve(root.left, maxSum);
        int[] right = solve(root.right, maxSum);
        if(root.val > left[1] && root.val < right[0]){
            int currSum = root.val + left[2] + right[2];
            maxSum[0] = Math.max(maxSum[0], currSum);
            int mini = Math.min(left[0], root.val);
            int maxi = Math.max(right[1], root.val);
            return new int[]{mini, maxi, currSum};
        }
        return new int[]{Integer.MIN_VALUE, Integer.MAX_VALUE, 0};//invalid bst  
    }
}
```
