# [Number of Good Leaf Nodes Pairs](https://leetcode.com/problems/number-of-good-leaf-nodes-pairs/)
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
    public int countPairs(TreeNode root, int distance) {
        HashSet<TreeNode> leafNodes = new HashSet<>();
        HashMap<TreeNode, TreeNode> parentMap = new HashMap<>();
        solve(root, parentMap, leafNodes);
        int count = 0;
        for(TreeNode leafNode : leafNodes){
            count += bfs(leafNode, parentMap, distance);
        }
        return count/2;//pairs are counted twice so dividing by 2    
    }
    public int bfs(TreeNode node, HashMap<TreeNode, TreeNode> parentMap, int distance){//counts total valid leaf nodes from the initial leaf node
        Queue<TreeNode> q = new LinkedList<>();
        q.add(node);
        int count = 0;
        int level = 0;
        HashSet<TreeNode> vis = new HashSet<>();
        vis.add(node);
        while(!q.isEmpty()){
            int size = q.size();
            while(size-- > 0){
                TreeNode curr = q.poll();
                if(curr.left == null && curr.right == null && level <= distance){
                    count++;
                }
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
                level++;
            }
        }
        return count-1;//-1 as the starting leaf node is itself getting counted
    }
    public void solve(TreeNode root, HashMap<TreeNode, TreeNode> map, HashSet<TreeNode> set){//adds leaf nodes in set and connects parent to child via map
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
            if(curr.left == null && curr.right == null){
                set.add(curr);
            }
        }   
    }
}
```
