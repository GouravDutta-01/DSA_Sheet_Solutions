# [K-diff Pairs in an Array](https://leetcode.com/problems/k-diff-pairs-in-an-array/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int findPairs(int[] nums, int k) {
        Arrays.sort(nums);
        int n = nums.length;
        int count = 0;
        HashSet<String> set = new HashSet<>();
        for(int i=0; i<n; i++){
            for(int j=i+1; j<n; j++){
                if(Math.abs(nums[i]-nums[j]) == k){
                    set.add(String.valueOf(nums[i]) + String.valueOf(nums[j]));
                }
            }
        }
        return set.size();  
    }
}
```
