# [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int maxSubArray(int[] nums) {
        boolean allNeg = true;
        int maxi = Integer.MIN_VALUE;
        int maxVal = Integer.MIN_VALUE;
        int currSum = 0;
        for(int i=0; i<nums.length; i++){
            if(allNeg && nums[i] >= 0){
                allNeg = false;
            }
            currSum += nums[i];
            if(currSum < 0){
                currSum = 0;
            }
            maxi = Math.max(maxi, currSum);
            maxVal = Math.max(nums[i], maxVal);//tracks array maximum for case when all array elements are negative
        }
        return allNeg ? maxVal : maxi;
    }
}
```
