# [Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)
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
    public int kthSmallest(TreeNode root, int k) {
        PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
        inorder(root, k, pq);
        return pq.peek();
    }
    public void inorder(TreeNode root, int k, PriorityQueue<Integer> pq){
        if(root == null){
            return;
        }
        inorder(root.left, k, pq);
        pq.add(root.val);
        if(pq.size() > k){
            pq.poll();
        }
        inorder(root.right, k, pq);
    }
}
```
