# [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
**Difficulty:** Easy

### Solution in Java
```java
class Solution {
    public int maxProfit(int[] prices) {
        int maxi = 0;
        int currMini = prices[0];
        for(int i=1; i<prices.length; i++){
            maxi = Math.max(prices[i]-currMini, maxi);
            currMini = Math.min(currMini, prices[i]);
        }
        return maxi;
    }
}
```
