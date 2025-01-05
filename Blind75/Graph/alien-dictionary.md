# [Alien Dictionary](https://www.geeksforgeeks.org/problems/alien-dictionary/1)
**Difficulty:** Hard

### Solution in Java
```java
class Solution {
    public String findOrder(String[] dict, int k) {
        List<List<Integer>> adjList = new ArrayList<>();
        for(int i=0; i<k; i++){
            adjList.add(new ArrayList<>());
        }
        int[] inorder = new int[k];
        for(int i=0; i+1<dict.length; i++){
            String first = dict[i];
            String second = dict[i+1];
            int ind = 0;
            while(ind < first.length() && ind < second.length() && first.charAt(ind) == second.charAt(ind)){
                ind++;//finding first character mismatch
            }
            if(ind == first.length() || ind == second.length()){
                if(first.length() > second.length()){//invalid dictionary
                    return "";
                }
                continue;
            }
            int firstInd = first.charAt(ind)-'a';
            int secondInd = second.charAt(ind)-'a';
            adjList.get(firstInd).add(secondInd);
            inorder[secondInd]++;
        }
        Queue<Integer> q = new LinkedList<>();
        StringBuilder topoOrder = new StringBuilder();
        for(int i=0; i<k; i++){
            if(inorder[i] == 0){
                q.add(i);
            }
        }
        while(!q.isEmpty()){
            int curr = q.poll();
            topoOrder.append((char)(curr+'a'));
            for(int neighbor : adjList.get(curr)){
                inorder[neighbor]--;
                if(inorder[neighbor] == 0){
                    q.add(neighbor);
                }
            }
        }
        return topoOrder.length() == k ? topoOrder.toString() : "";
    }
}
```
