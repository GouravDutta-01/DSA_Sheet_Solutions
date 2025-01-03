# [Random Point in Non-overlapping Rectangles](https://leetcode.com/problems/random-point-in-non-overlapping-rectangles/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    int[][] rects;
    TreeMap<Integer, Integer> map;
    int totalPoints;
    public Solution(int[][] rects) {
        totalPoints = 0;
        map = new TreeMap<>();
        this.rects = rects;
        int ind = 0;
        for(int[] rect : rects){
            totalPoints += (rect[2]-rect[0]+1)*(rect[3]-rect[1]+1);
            map.put(totalPoints, ind++);
        }
    }
    
    public int[] pick() {
        int randomKey = map.ceilingKey((int)(Math.random()*totalPoints+1));
        int[] temp = rects[map.get(randomKey)];
        int xRandom = temp[0] + (int)(Math.random()*(temp[2]-temp[0]+1));
        int yRandom = temp[1] + (int)(Math.random()*(temp[3]-temp[1]+1));
        return new int[]{xRandom, yRandom};    
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(rects);
 * int[] param_1 = obj.pick();
 */
```
