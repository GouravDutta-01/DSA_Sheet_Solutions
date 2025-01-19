# [Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)
**Difficulty:** Hard

### Solution in Java
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Codec {

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        if(root == null){
            return "";
        }
        StringBuilder sb = new StringBuilder();
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);
        sb.append(root.val).append(",");
        while(!q.isEmpty()){
            TreeNode curr = q.poll();
            if(curr.left != null){
                q.add(curr.left);
                sb.append(curr.left.val).append(",");
            }
            else{
                sb.append("#").append(",");
            }
            if(curr.right != null){
                q.add(curr.right);
                sb.append(curr.right.val).append(",");
            }
            else{
                sb.append("#").append(",");
            }
        }
        return sb.toString();
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        if(data == ""){
            return null;
        }
        String[] tokens = data.split(",");
        TreeNode root = new TreeNode(Integer.parseInt(tokens[0]));
        int ind = 1;
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);
        while(ind < tokens.length){
            TreeNode curr = q.poll();
            if(!tokens[ind].equals("#")){
                curr.left = new TreeNode(Integer.parseInt(tokens[ind]));
                q.add(curr.left);
            }
            ind++;
            if(ind < tokens.length && !tokens[ind].equals("#")){
                curr.right = new TreeNode(Integer.parseInt(tokens[ind]));
                q.add(curr.right);
            }
            ind++;
        }
        return root;
    }
}

// Your Codec object will be instantiated and called as such:
// Codec ser = new Codec();
// Codec deser = new Codec();
// TreeNode ans = deser.deserialize(ser.serialize(root));
```
