# [Amount of Time for Binary Tree to Be Infected](https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected/)
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
    public int amountOfTime(TreeNode root, int start) {
        TreeNode startNode = findNode(root, start);
        HashMap<TreeNode, TreeNode> parentMap = connectParent(root);
        Queue<TreeNode> q = new LinkedList<>();
        q.add(startNode);
        HashSet<TreeNode> vis = new HashSet<>();
        vis.add(startNode);
        int time = 0;
        while(!q.isEmpty()){
            int size = q.size();
            while(size-- > 0){
                TreeNode curr = q.poll();
                if(curr.left != null && !vis.contains(curr.left)){
                    q.add(curr.left);
                    vis.add(curr.left);
                }
                if(curr.right != null && !vis.contains(curr.right)){
                    q.add(curr.right);
                    vis.add(curr.right);
                }
                if(parentMap.containsKey(curr) && !vis.contains(parentMap.get(curr))){
                    q.add(parentMap.get(curr));
                    vis.add(parentMap.get(curr));
                }
            }
            if(!q.isEmpty()){
                time++;
            }
        }
        return time;    
    }
    public HashMap<TreeNode, TreeNode> connectParent(TreeNode root){
        HashMap<TreeNode, TreeNode> map = new HashMap<>();
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);
        while(!q.isEmpty()){
            TreeNode curr = q.poll();
            if(curr.left != null){
                q.add(curr.left);
                map.put(curr.left, curr);
            }
            if(curr.right != null){
                q.add(curr.right);
                map.put(curr.right, curr);
            }
        }
        return map;
    }
    public TreeNode findNode(TreeNode root, int start){
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);
        while(!q.isEmpty()){
            TreeNode curr = q.poll();
            if(curr.val == start){
                return curr;
            }
            if(curr.left != null){
                q.add(curr.left);
            }
            if(curr.right != null){
                q.add(curr.right);
            }
        }
        return null;
    }
}
```
