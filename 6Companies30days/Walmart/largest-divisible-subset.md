# [Largest Divisible Subset](https://leetcode.com/problems/largest-divisible-subset/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public List<Integer> largestDivisibleSubset(int[] nums) {
        int n = nums.length;
        Arrays.sort(nums);
        int[] dp = new int[n];
        int[] parent = new int[n];
        int maxLen = 0;
        int lastInd = -1;
        for(int i=0; i<n; i++){
            dp[i] = 1;
            parent[i] = i;
            for(int j=0; j<i; j++){
                if(nums[i] % nums[j] == 0 && dp[j] + 1 > dp[i]){
                    dp[i] = 1 + dp[j];
                    parent[i] = j;
                }
            }
            if(dp[i] > maxLen){
                maxLen = dp[i];
                lastInd = i;
            }
        }
        List<Integer> lds = new ArrayList<>();
        lds.add(nums[lastInd]);
        while(parent[lastInd] != lastInd){
            lds.add(nums[parent[lastInd]]);
            lastInd = parent[lastInd];
        }
        Collections.sort(lds, Collections.reverseOrder());
        return lds;
    }
}
```
### Note:
- Similar to printing largest increasing subsequence
