# [Maximum Sum of Distinct Subarrays With Length K](https://leetcode.com/problems/maximum-sum-of-distinct-subarrays-with-length-k/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public long maximumSubarraySum(int[] nums, int k) {
        int n = nums.length;
        long currSum = 0;
        long maxSum = 0;
        HashMap<Integer, Integer> map = new HashMap<>();
        int left = 0;
        int right = 0;
        while(right < k){
            currSum += nums[right];
            map.put(nums[right], map.getOrDefault(nums[right], 0) + 1);
            right++;
        }
        if(map.size() == k){
            maxSum = currSum;
        }
        while(right < n){
            currSum += (nums[right]-nums[left]);
            map.put(nums[right], map.getOrDefault(nums[right], 0) + 1);
            map.put(nums[left], map.get(nums[left])-1);
            if(map.get(nums[left]) == 0){
                map.remove(nums[left]);
            }
            left++;
            if(map.size() == k){
                maxSum = Math.max(maxSum, currSum);
            }
            right++;
        }
        return maxSum;  
    }
}
```
