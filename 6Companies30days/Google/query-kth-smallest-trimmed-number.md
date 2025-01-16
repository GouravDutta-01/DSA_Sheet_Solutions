# [Query Kth Smallest Trimmed Number](https://leetcode.com/problems/query-kth-smallest-trimmed-number/)
**Difficulty:** Medium

### Solution in Java
```java
class Pair{
    int ind;
    String str;
    public Pair(int ind, String str){
        this.ind = ind;
        this.str = str;
    }
}
class Solution {
    public int[] smallestTrimmedNumbers(String[] nums, int[][] queries) {
        int[] ans =  new int[queries.length];
        int k = 0;
        for(int[] query : queries){
            String[] temp = trimDigits(nums, query[1]);
            PriorityQueue<Pair> pq = new PriorityQueue<>((a, b) -> a.str.equals(b.str) ? b.ind - a.ind : b.str.compareTo(a.str));
            for(int i=0; i<temp.length; i++){
                pq.add(new Pair(i, temp[i]));
                if(pq.size() > query[0]){
                    pq.poll();
                }
            }
            ans[k++] = pq.peek().ind;
        }
        return ans;
    }
    public String[] trimDigits(String[] nums, int trim){
        int n = nums.length;
        int len = nums[0].length();
        String[] temp = new String[n];
        for(int i=0; i<n; i++){
            temp[i] = nums[i].substring(len-trim, len);
        }
        return temp;
    }
}
```
