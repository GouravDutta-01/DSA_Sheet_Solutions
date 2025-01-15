# [Maximum Length of Repeated Subarray](https://leetcode.com/problems/maximum-length-of-repeated-subarray/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int findLength(int[] nums1, int[] nums2) {
        int maxLen = 0;
        for(int i=0; i<nums1.length; i++){
            for(int j=0; j<nums2.length; j++){
                maxLen = Math.max(maxLen, solve(i, j, nums1, nums2));
            }
        }
        return maxLen;
    }
    public int solve(int i, int j, int[] nums1, int[] nums2){
        int len = 0;
        while(i < nums1.length && j < nums2.length){
            if(nums1[i] == nums2[j]){
                len++;
                i++;
                j++;
            }
            else{
                break;
            }
        }
        return len;
    }
}
```
