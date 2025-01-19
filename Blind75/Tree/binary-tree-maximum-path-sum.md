# [Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)
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
    public int maxPathSum(TreeNode root) {
        int[] maxSum = new int[1];
        boolean[] allNeg = new boolean[1];
        allNeg[0] = true;//considering all nodes to be negative
        int[] maxVal = new int[1];//storing max val to return when all nodes are negative(similar to kadanes algo)
        maxVal[0] = Integer.MIN_VALUE;
        solve(root, maxSum, maxVal, allNeg);
        if(allNeg[0]){
            return maxVal[0];
        }
        return maxSum[0];
    }
    public int solve(TreeNode root, int[] maxSum, int[] maxVal, boolean[] allNeg){
        if(root == null){
            return 0;
        }
        int lMaxSum = Math.max(0, solve(root.left, maxSum, maxVal, allNeg));//return 0 when path sum on that path is negative to not consider that path
        int rMaxSum = Math.max(0, solve(root.right, maxSum, maxVal, allNeg));
        maxSum[0] = Math.max(maxSum[0], lMaxSum + rMaxSum + root.val);
        maxVal[0] = Math.max(root.val, maxVal[0]);
        if(root.val > 0){
            allNeg[0] = false;
        }
        return root.val + Math.max(lMaxSum, rMaxSum);
    }
}
```
