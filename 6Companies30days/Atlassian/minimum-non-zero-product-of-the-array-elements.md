# [Minimum Non-Zero Product of the Array Elements](https://leetcode.com/problems/minimum-non-zero-product-of-the-array-elements/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int minNonZeroProduct(int p) {
        long mod = (long)Math.pow(10, 9)+7;
        long maxVal = (1L<<p)-1;//this is the last value of the given range [1, 2^p-1]
        //All values except the maxVal will form (maxVal-1)/2 pairs among themselves. The pairs will be inverse of each other and will swap digits between them such that each pair will obtain (maxVal-1) as minimum pair product.
        long others = solve((maxVal-1)%mod, (maxVal-1)/2, mod);//not using Math.pow() as result will overflow
        return (int)(((maxVal%mod)*(others%mod))%mod);    
    }
    public long solve(long base, long exp, long mod){
        if(exp == 0){
            return 1L;
        }
        if(exp%2 == 0){
            return solve((base*base)%mod, exp/2, mod);
        }
        return (base*solve(base, exp-1, mod))%mod;
    }
}
```
