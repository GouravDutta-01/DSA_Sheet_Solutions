# [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for(int val : nums){
            map.put(val, map.getOrDefault(val, 0) + 1);
        }
        PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> a[1] - b[1]);//min heap on basis of element frequency
        for(Map.Entry<Integer, Integer> entry : map.entrySet()){
            pq.add(new int[]{entry.getKey(), entry.getValue()});
            if(pq.size() > k){
                pq.poll();
            }
        }
        int[] ans = new int[k];
        int ind = 0;
        while(!pq.isEmpty()){
            ans[ind++] = pq.poll()[0];
        }
        return ans;    
    }
}
```
