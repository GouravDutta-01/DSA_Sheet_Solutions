# [Reverse Bits](https://leetcode.com/problems/reverse-bits/)
**Difficulty:** Easy

### Solution in Java
```java
public class Solution {
    // you need treat n as an unsigned value
    public int reverseBits(int n) {
        int ans = 0;
        for(int i=0; i<32; i++){
            int leftBit = ((1 << i) & n);
            int rightBit = ((1 << (31-i)) & n);
            if(leftBit != 0){
                ans = (ans | (1 << (31-i)));//setting the right bit if left bit is 1
            }
            if(rightBit != 0){
                ans = (ans | (1 << i));//setting the left bit if right bit is 1
            }
        }
        return ans;
    }
}
```
