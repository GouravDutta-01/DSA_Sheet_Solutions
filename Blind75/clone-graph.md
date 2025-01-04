# [Clone Graph](https://leetcode.com/problems/clone-graph/)
**Difficulty:** Medium

### Solution in Java
```java
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> neighbors;
    public Node() {
        val = 0;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val) {
        val = _val;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val, ArrayList<Node> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
}
*/

class Solution {
    public Node cloneGraph(Node node) {
        if(node == null){
            return null;
        }
        HashMap<Node, Node> map = new HashMap<>();
        Queue<Node> q = new LinkedList<>();
        map.put(node, new Node(node.val));
        q.add(node);
        while(!q.isEmpty()){
            Node curr = q.poll();
            Node cloneNode = map.get(curr);
            for(Node neighbor : curr.neighbors){
                if(map.containsKey(neighbor)){
                    cloneNode.neighbors.add(map.get(neighbor));
                }
                else{
                    map.put(neighbor, new Node(neighbor.val));
                    cloneNode.neighbors.add(map.get(neighbor));
                    q.add(neighbor);
                }
            }
        }
        return map.get(node);   
    }
}
```
