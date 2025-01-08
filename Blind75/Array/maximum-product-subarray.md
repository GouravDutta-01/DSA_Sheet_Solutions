# [Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int maxProduct(int[] nums) {
        int n = nums.length;
        int prefix = 1;
        int suffix = 1;
        int maxi = Integer.MIN_VALUE;
        for(int i=0; i<n; i++){
            prefix *= nums[i];
            suffix *= nums[n-i-1];
            maxi = Math.max(maxi, Math.max(suffix, prefix));
            if(prefix == 0){//reset as no benefit in taking zero
                prefix = 1;
            }
            if(suffix == 0){
                suffix = 1;
            }
        }
        return maxi;
    }
}
```
