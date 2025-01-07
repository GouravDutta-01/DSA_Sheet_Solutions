# [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)
**Difficulty:** Easy

### Solution in Java
```java
class Solution {
    public int hammingWeight(int n) {
        int count = 0;
        while(n > 0){
            n = n & (n-1);//turns off the rightmost set bit
            count++;
        }
        return count;
    }
}
```
