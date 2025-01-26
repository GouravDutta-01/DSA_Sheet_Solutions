# [Random Flip Matrix](https://leetcode.com/problems/random-flip-matrix/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    HashMap<Integer, Integer> map;
    int m;
    int n;
    int countZeroes;

    public Solution(int m, int n) {
        map = new HashMap<>();
        this.m = m;
        this.n = n;
        countZeroes = m*n;        
    }
    
    public int[] flip() {
        int randomInd = (int)(Math.random()*countZeroes);
        int actualInd = map.getOrDefault(randomInd, randomInd);
        countZeroes--;
        map.put(randomInd, map.getOrDefault(countZeroes, countZeroes));
        return new int[]{actualInd/n, actualInd%n};
    }
    
    public void reset() {
        map.clear();
        countZeroes = m*n;
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(m, n);
 * int[] param_1 = obj.flip();
 * obj.reset();
 */
```
