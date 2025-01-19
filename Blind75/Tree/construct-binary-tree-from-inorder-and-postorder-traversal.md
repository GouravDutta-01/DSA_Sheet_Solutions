# [Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/)
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
    public TreeNode buildTree(int[] inorder, int[] postorder) {
        int n = inorder.length;
        HashMap<Integer, Integer> map = new HashMap<>();
        for(int i=0; i<n; i++){
            map.put(inorder[i], i);
        }
        return buildTreeHelper(0, n-1, 0, n-1, inorder, postorder, map);
    }
    public TreeNode buildTreeHelper(int is, int ie, int ps, int pe, int[] inorder, int[] postorder, HashMap<Integer, Integer> map){
        if(is > ie || ps > pe){
            return null;
        }
        TreeNode root = new TreeNode(postorder[pe]);
        int rootInd = map.get(postorder[pe]);
        int countLeft = rootInd-is;
        root.left = buildTreeHelper(is, rootInd-1, ps, ps+countLeft-1, inorder, postorder, map);
        root.right = buildTreeHelper(rootInd+1, ie, ps+countLeft, pe-1, inorder, postorder, map);
        return root;
    }
}
```
