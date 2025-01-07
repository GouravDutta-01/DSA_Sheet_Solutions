# [Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int getSum(int a, int b) {
        while(b != 0){
            int temp = a;
            a = a ^ b;//for storing result without carry
            b = (temp & b) << 1;//for storing carry
        }
        return a;
    }
}
```
