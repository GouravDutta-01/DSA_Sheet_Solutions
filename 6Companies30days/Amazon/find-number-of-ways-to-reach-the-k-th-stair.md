# [Find Number of Ways to Reach the K-th Stair](https://leetcode.com/problems/find-number-of-ways-to-reach-the-k-th-stair/)
**Difficulty:** Hard

### Solution 1 in Java (Memoization)
```java
class Solution {
    public int waysToReachStair(int k) {
        int[] power = new int[32];//precomputes power of 2
        power[0] = 1;
        for(int i=1; i<32; i++){
            power[i] = 2*power[i-1];
        }
        HashMap<String, Integer> dp = new HashMap<>();
        return solve(1, 0, 1, k, dp, power);
    }
    public int solve(int i, int jump, int back, int k, HashMap<String, Integer> dp, int[] power){
        if(i >= k+2){
            return 0;
        }
        String key = i + "-" + jump + "-" + back;
        if(dp.containsKey(key)){
            return dp.get(key);
        }
        int count = 0;
        if(i == k){
            count++;
        }
        if(i != 0 && back == 1){
            count += solve(i-1, jump, 0, k, dp, power);
        }
        count += solve(i+(int)Math.pow(2, jump), jump+1, 1, k, dp, power);
        dp.put(key, count);
        return count;
    }
}
```
### Note:
- Time Complexity : O(logk) due to exponential forward jumps
- Space Complexity : O(logk) for recursion stack and map storage
- Using map for memoization for avoiding MLE as state space is sparse
- Precomputing power of 2 for better efficiency
