# [Count the Number of Square-Free Subsets](https://leetcode.com/problems/count-the-number-of-square-free-subsets/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int squareFreeSubsets(int[] nums) {
        int mod = (int)1e9+7;
        HashSet<Integer> inValid = new HashSet<>();
        for(int i=2; i<6; i++){//adding the numbers which are squares or multiple of it in set
            int sq = i*i;
            for(int j=sq; j<=30; j+=sq){
                inValid.add(j);
            }
        }
        int[] freq = new int[31];
        for(int val : nums){
            freq[val]++;
        }
        List<Integer> valid = new ArrayList<>();
        for(int i=1; i<=30; i++){
            if(freq[i] > 0 && !inValid.contains(i)){
                valid.add(i);
            }
        }
        int n = valid.size();
        long oneCombination = 1;
        if(freq[1] > 0){
            oneCombination = getPower(2, freq[1], mod)-1;//all non empty subsets of 1
        }
        long ans = 0;
        for(int i=1; i<(1<<n); i++){//checking every subsets with valid numbers
            boolean sqFree = true;
            long product = 1;
            long subSeqCount = 1;//ways to form the current subset
            long countOne = 1;
            for(int j=0; j<n; j++){
                if(((1<<j)&i) != 0){//checking if j-th number is included in the subset
                    if(findGCD(product, (long)valid.get(j)) > 1){
                        sqFree = false;//current subset is not square free
                        break;
                    }
                    product *= valid.get(j);
                    if(valid.get(j) != 1){
                        subSeqCount = (subSeqCount*freq[valid.get(j)])%mod;
                    }
                    else{
                        countOne = oneCombination;
                    }
                }
            }
            if(sqFree){
                subSeqCount = (subSeqCount*countOne)%mod;
                ans = (ans+subSeqCount)%mod;
            }
        }
        return (int)ans;
    }
    public long findGCD(long a, long b){
        if(b == 0){
            return a;
        }
        return findGCD(b, a%b);
    }
    public long getPower(long a, long b, int mod){
        long result = 1;
        for(int i=0; i<b; i++){
            result = (a*result)%mod;
        }
        return result;
    }
}
```
