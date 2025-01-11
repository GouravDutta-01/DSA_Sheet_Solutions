# [Find Subsequence of Length K With the Largest Sum](https://leetcode.com/problems/find-subsequence-of-length-k-with-the-largest-sum/)
**Difficulty:** Easy

### Solution in Java
```java
class Solution {
    public int[] maxSubsequence(int[] nums, int k) {
        PriorityQueue<int[]> pq1 = new PriorityQueue<>((a, b) -> a[0] - b[0]);
        for(int i=0; i<nums.length; i++){
            pq1.add(new int[]{nums[i], i});
            if(pq1.size() > k){
                pq1.poll();
            }
        }
        PriorityQueue<int[]> pq2 = new PriorityQueue<>((a, b) -> a[1] - b[1]);
        while(!pq1.isEmpty()){
            pq2.add(pq1.poll());
        }
        int ind = 0;
        int[] ans = new int[k];
        while(!pq2.isEmpty()){
            ans[ind++] = pq2.poll()[0];
        }
        return ans;   
    }
}
```
