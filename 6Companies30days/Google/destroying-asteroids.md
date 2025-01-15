# [Destroying Asteroids](https://leetcode.com/problems/destroying-asteroids/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public boolean asteroidsDestroyed(int mass, int[] asteroids) {
        Arrays.sort(asteroids);
        long sum = mass;
        for(int i=0; i<asteroids.length; i++){
            if(sum < asteroids[i]){
                return false;
            }
            sum += asteroids[i];
        }
        return true;
    }
}
```
