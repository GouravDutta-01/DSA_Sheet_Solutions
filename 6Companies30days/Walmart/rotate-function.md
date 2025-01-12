# [Rotate Function](https://leetcode.com/problems/rotate-function/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int maxRotateFunction(int[] nums) {
        int n = nums.length;
        int sum = 0;
        for(int val : nums){
            sum += val;
        }
        int prev = 0;
        for(int i=0; i<n; i++){
            prev += i*nums[i];
        }
        int maxi = prev;
        for(int i=1; i<n; i++){
            int curr = prev + sum - n*nums[n-i];
            prev = curr;
            maxi = Math.max(maxi, curr);
        }
        return maxi;
    }
}
```
