# [Count the Number of Incremovable Subarrays I](https://leetcode.com/problems/count-the-number-of-incremovable-subarrays-i/)
**Difficulty:** Easy

### Solution in Java
```java
class Solution {
    public int incremovableSubarrayCount(int[] nums) {
        int n = nums.length;
        int count = 0;
        for(int i=0; i<n; i++){
            for(int j=i; j<n; j++){
                boolean flag = true;
                int prev = -1;
                for(int k=0; k<n; k++){
                    if(k < i || k > j){
                        if(nums[k] <= prev){
                            flag = false;
                            break;
                        }
                        else{
                            prev = nums[k];
                        }
                    }
                }
                if(flag){
                    count++;
                }
            }
        }
        return count;
    }
}
```
