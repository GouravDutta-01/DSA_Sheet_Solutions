# [Graph is Tree or Not](https://www.geeksforgeeks.org/problems/is-it-a-tree/0)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public boolean isTree(int n, int m, ArrayList<ArrayList<Integer>> edges) 
    {
        ArrayList<ArrayList<Integer>> adjList = new ArrayList<>();
        for(int i=0; i<n; i++){
            adjList.add(new ArrayList<>());
        }
        for(ArrayList<Integer> edge : edges){
            int u = edge.get(0);
            int v = edge.get(1);
            adjList.get(u).add(v);
            adjList.get(v).add(u);
        }
        boolean[] vis = new boolean[n];
        if(dfs(0, -1, vis, adjList)){
            return false;//graph has cycle
        }
        for(boolean val : vis){
            if(val == false){
                return false;//graph is disconnected
            }
        }
        return true;
    }
    public boolean dfs(int node, int parent, boolean[] vis, ArrayList<ArrayList<Integer>> adjList){//returns true if graph has cycle
        vis[node] = true;
        for(int neighbor : adjList.get(node)){
            if(!vis[neighbor]){
                if(dfs(neighbor, node, vis, adjList)){
                    return true;
                }
            }
            else if(neighbor != parent){
                return true;
            }
        }
        return false;
    }
}
```
