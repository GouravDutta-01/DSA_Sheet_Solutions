# [Course Schedule](https://leetcode.com/problems/course-schedule/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        List<List<Integer>> adjList = new ArrayList<>();
        for(int i=0; i<numCourses; i++){
            adjList.add(new ArrayList<>());
        }
        int[] inorder = new int[numCourses];
        for(int[] val : prerequisites){
            int a = val[0];
            int b = val[1];
            adjList.get(b).add(a);
            inorder[a]++;
        }
        Queue<Integer> q = new LinkedList<>();
        for(int i=0; i<numCourses; i++){
            if(inorder[i] == 0){
                q.add(i);
            }
        }
        int count = 0;
        while(!q.isEmpty()){
            int curr = q.poll();
            count++;
            for(int neighbor : adjList.get(curr)){
                inorder[neighbor]--;
                if(inorder[neighbor] == 0){
                    q.add(neighbor);
                }
            }
        }
        return count == numCourses;
    }
}
```
