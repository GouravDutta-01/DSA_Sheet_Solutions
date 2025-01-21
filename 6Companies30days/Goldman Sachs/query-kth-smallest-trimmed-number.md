# [Query Kth Smallest Trimmed Number](https://leetcode.com/problems/query-kth-smallest-trimmed-number/)
**Difficulty:** Medium

### Solution in Java
```java
class Pair{
    String str;
    int ind;
    public Pair(String str, int ind){
        this.str = str;
        this.ind = ind;
    }
}
class Solution {
    public int[] smallestTrimmedNumbers(String[] nums, int[][] queries) {
        int[] ans = new int[queries.length];
        int ind = 0;
        for(int[] query : queries){
            PriorityQueue<Pair> pq = new PriorityQueue<>((a, b) -> a.str.equals(b.str) ? b.ind - a.ind : b.str.compareTo(a.str));
            int k = query[0];
            int trim = query[1];
            int i = 0;
            for(String val : nums){
                String s = val.substring(val.length()-trim, val.length());
                pq.add(new Pair(s, i));
                if(pq.size() > k){
                    pq.poll();
                }
                i++;
            }
            ans[ind++] = pq.peek().ind;
        }
        return ans;
    }
}
```