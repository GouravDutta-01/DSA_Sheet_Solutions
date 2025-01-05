# [Connected Components in an Undirected Graph](https://www.geeksforgeeks.org/problems/connected-components-in-an-undirected-graph/1)
**Difficulty:** Medium

### Solution in Java
```java
class DSU{
    int[] parent;
    int[] rank;
    public DSU(int size){
        parent = new int[size+1];
        rank = new int[size+1];
        for(int i=0; i<size+1; i++){
            parent[i] = i;
        }
    }
    public int findParent(int i){
        if(i == parent[i]){
            return i;
        }
        return parent[i] = findParent(parent[i]);
    }
    public void union(int x, int y){
        int parentX = findParent(x);
        int parentY = findParent(y);
        if(parentX == parentY){
            return;
        }
        if(rank[parentX] > rank[parentY]){
            parent[parentY] = parentX;
        }
        else if(rank[parentX] < rank[parentY]){
            parent[parentX] = parentY;
        }
        else{
            parent[parentX] = parentY;
            rank[parentY]++;
        }
    }
}
class Solution {
    public ArrayList<ArrayList<Integer>> connectedcomponents(int v, int[][] edges) {
        DSU obj = new DSU(v);
        for(int[] edge : edges){
            int a = edge[0];
            int b = edge[1];
            obj.union(a, b);
        }
        HashMap<Integer, ArrayList<Integer>> map = new HashMap<>();
        for(int i=0; i<v; i++){
            int parent = obj.findParent(i);
            if(!map.containsKey(parent)){
                map.put(parent, new ArrayList<>());
            }
            map.get(parent).add(i);
        }
        ArrayList<ArrayList<Integer>> ans = new ArrayList<>(map.values());
        return ans;
    }
}
```
