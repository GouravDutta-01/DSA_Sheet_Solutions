# [Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int numberOfSubarrays(int[] nums, int k) {
        int n = nums.length;
        return solve(nums, k, n) - solve(nums, k-1, n);
    }
    public int solve(int[] nums, int k, int n){//counts subarray having odd numbers less than or equal to k
        int countOdd = 0;
        int left = 0;
        int right = 0;
        int count = 0;
        while(right < n){
            if(nums[right] % 2 != 0){
                countOdd++;
            }
            while(countOdd > k){
                if(nums[left] % 2 != 0){
                    countOdd--;
                }
                left++;
            }
            count += right-left+1;
            right++;
        }
        return count; 
    }
}
```
