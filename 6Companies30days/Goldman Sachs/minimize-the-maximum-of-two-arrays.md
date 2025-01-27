# [Minimize the Maximum of Two Arrays](https://leetcode.com/problems/minimize-the-maximum-of-two-arrays/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int minimizeSet(int divisor1, int divisor2, int uniqueCnt1, int uniqueCnt2) {
        long lcm = findLCM(divisor1, divisor2);
        long low = 1;
        long high = (int)1e9*2;
        long ans = -1;
        while(low <= high){
            long mid = low + (high-low)/2;
            long common = mid/lcm;//divisible by both divisor1 and divisor2
            long only1 = (long)mid/divisor1-common;//only divisible by divisor1 and not divisor2
            long only2 = (long)mid/divisor2-common;//only divisible by divisor2 and not divisor1
            long availableForAll = mid-common-only1-only2;//divisible by neither divisor1 nor divisor2
            //we will first try to fill numbers only divisible by divisor2 in arr1 and numbers only divisible by divisor1 in arr2
            long remNeeded = Math.max(0, uniqueCnt1-only2) + Math.max(0, uniqueCnt2-only1);
            if(availableForAll >= remNeeded){
                ans = mid;
                high = mid-1;
            }
            else{
                low = mid+1;
            }
        }
        return (int)ans;
    }
    public long findLCM(int a, int b){
        return (long)a*(b/findGCD(a, b));
    }
    public long findGCD(int a, int b){
        if(b == 0){
            return a;
        }
        return findGCD(b, a%b);
    }
}
```
