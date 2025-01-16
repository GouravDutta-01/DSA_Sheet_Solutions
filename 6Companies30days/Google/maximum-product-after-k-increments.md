# [Maximum Product After K Increments](https://leetcode.com/problems/maximum-product-after-k-increments/)
**Difficulty:** Medium

### Solution in Java
```java
class Pair{
    int ind;
    int val;
    public Pair(int ind, int val){
        this.ind = ind;
        this.val = val;
    }
}
class Solution {
    public int maximumProduct(int[] nums, int k) {
        int mod = (int)1e9+7;
        PriorityQueue<Pair> pq = new PriorityQueue<>((a, b) -> a.val - b.val);
        for(int i=0; i<nums.length; i++){
            pq.add(new Pair(i, nums[i]));
        }
        while(k-- > 0){
            Pair curr = pq.poll();
            nums[curr.ind] = curr.val+1;
            pq.add(new Pair(curr.ind, nums[curr.ind]));
        }
        long maxi = 1;
        for(int val : nums){
            maxi = (maxi%mod)*(val%mod)%mod;
        }
        return (int)maxi%mod;
    }
}
```
