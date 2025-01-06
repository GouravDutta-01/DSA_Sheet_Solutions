# [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)
**Difficulty:** Medium

### Solution in Java
```java
class Pair{
    int x;
    int y;
    public Pair(int x, int y){
        this.x = x;
        this.y = y;
    }
}
class Solution {
    public int orangesRotting(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int[][] directions = new int[][]{{0, 1}, {0, -1}, {1, 0}, {-1, 0}};
        Queue<Pair> q = new LinkedList<>();
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(grid[i][j] == 2){
                    q.add(new Pair(i, j));//adding the rotten oranges
                }
            }
        }
        int time = 0;
        while(!q.isEmpty()){
            int size = q.size();
            while(size-- > 0){
                Pair curr = q.poll();
                for(int[] direction : directions){
                    int r = curr.x + direction[0];
                    int c = curr.y + direction[1];
                    if(r >= 0 && c >= 0 && r < m && c < n && grid[r][c] == 1){
                        grid[r][c] = 2;//rotting the fresh oranges
                        q.add(new Pair(r, c));
                    }
                }
            }
            if(!q.isEmpty()){
                time++;
            }
        }
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(grid[i][j] == 1){
                    return -1;
                }
            }
        }
        return time;    
    }
}
```
