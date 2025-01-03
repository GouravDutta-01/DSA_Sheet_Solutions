# [Shopping Offers](https://leetcode.com/problems/shopping-offers/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int shoppingOffers(List<Integer> price, List<List<Integer>> special, List<Integer> needs) {
        int n = price.size();
        HashMap<List<Integer>, Integer> dp = new HashMap<>();
        return solve(price, special, needs, n, dp);
    }
    public int solve(List<Integer> price, List<List<Integer>> special, List<Integer> needs, int n, HashMap<List<Integer>, Integer> dp){
        if(dp.containsKey(needs)){
            return dp.get(needs);
        }
        int minCost = 0;
        for(int i=0; i<n; i++){
            minCost += needs.get(i)*price.get(i);
        }
        for(List<Integer> offer : special){
            boolean isValid = true;
            for(int i=0; i<n; i++){
                if(needs.get(i) < offer.get(i)){
                    isValid = false;
                }
            }
            if(isValid){
                for(int i=0; i<n; i++){
                    needs.set(i, needs.get(i)-offer.get(i));
                }
                minCost = Math.min(minCost, offer.get(n)+solve(price, special, needs, n, dp));
                for(int i=0; i<n; i++){
                    needs.set(i, needs.get(i)+offer.get(i));
                }
            }
        }
        dp.put(needs, minCost);
        return minCost;  
    }
}
```
