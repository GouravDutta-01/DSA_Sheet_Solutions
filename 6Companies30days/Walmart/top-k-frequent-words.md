# [Top K Frequent Words](https://leetcode.com/problems/top-k-frequent-words/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
        HashMap<String, Integer> map = new HashMap<>();
        for(String word : words){
            map.put(word, map.getOrDefault(word, 0) + 1);
        }
        PriorityQueue<String> pq = new PriorityQueue<>((a, b) -> map.get(a) == map.get(b) ? b.compareTo(a) : map.get(a) - map.get(b));//min heap wrt freq of words and if freq same then in reverse lexicographic order
        for(Map.Entry<String, Integer> entry : map.entrySet()){
            pq.add(entry.getKey());
            if(pq.size() > k){
                pq.poll();
            }
        }
        List<String> ans = new ArrayList<>();
        while(!pq.isEmpty()){
            ans.add(pq.poll());
        }
        Collections.sort(ans, (a, b) -> map.get(a) == map.get(b) ? a.compareTo(b) : map.get(b) - map.get(a));
        return ans;
    }
}
```
