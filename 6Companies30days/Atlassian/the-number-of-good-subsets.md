# [The Number of Good Subsets](https://leetcode.com/problems/the-number-of-good-subsets/)
**Difficulty:** Hard

### Solution in Java
```java
class Solution {
    public int numberOfGoodSubsets(int[] nums) {
        int mod = (int)1e9+7;
        int[] primes = new int[]{2, 3, 5, 7, 11, 13, 17, 19, 23, 29};
        int[] freq = new int[31];
        for(int val : nums){
            freq[val]++;
        }
        int n = primes.length;
        long[] dp = new long[1<<n];// dp[i] represents the number of subsets with prime factors matching bitmask i
        dp[0] = 1;
        for(int i=0; i<freq[1]; i++){
            dp[0] = (dp[0]*2)%mod;
        }
        for(int i=2; i<31; i++){
            if(freq[i] == 0 || i%4 == 0 || i%9 == 0 || i%25 == 0){//neglecting nos. having no occurence or nos. having repeated prime factors
                continue;
            }
            int mask = 0;//mask for the prime factors of the current number
            for(int j=0; j<n; j++){
                if(i%primes[j] == 0){
                    mask = (mask | (1<<j));//adding jth prime
                }
            }
            for(int j=(1<<n)-1; j>0; j--){
                if((j&mask) == mask){ //update if the current mask can fit into the subset represented by j
                    dp[j] = (dp[j]+freq[i]*dp[j^mask])%mod;
                }
            }
        }
        long total = 0;
        for(int i=1; i<(1<<n); i++){
            total = (total+dp[i])%mod;
        }
        return (int)total;
    }
}
```
