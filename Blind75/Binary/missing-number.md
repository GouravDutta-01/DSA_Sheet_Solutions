# [Missing Number](https://leetcode.com/problems/missing-number/)
**Difficulty:** Easy

### Solution in Java
```java
class Solution {
    public int missingNumber(int[] nums) {
        int xor = 0;
        for(int i=0; i<nums.length; i++){//a^0 = a; a^a = 0
            xor ^= nums[i];
            xor ^= i;
        }
        xor ^= nums.length;
        return xor;   
    }
}
```
