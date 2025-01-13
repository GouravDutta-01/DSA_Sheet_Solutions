# [Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public String frequencySort(String s) {
        HashMap<Character, Integer> map = new HashMap<>();
        for(char ch : s.toCharArray()){
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }
        PriorityQueue<Character> pq = new PriorityQueue<>((a, b) -> map.get(b) - map.get(a));
        for(Map.Entry<Character, Integer> entry : map.entrySet()){
            pq.add(entry.getKey());
        }
        StringBuilder sb = new StringBuilder();
        while(!pq.isEmpty()){
            char curr = pq.poll();
            int freq = map.get(curr);
            while(freq-- > 0){
                sb.append(curr);
            }
        }
        return sb.toString();
    }
}
```
