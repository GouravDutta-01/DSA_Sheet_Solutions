# [Russian Doll Envelopes](https://leetcode.com/problems/russian-doll-envelopes/)
**Difficulty:** Hard

### Solution in Java
```java
class Solution {
    public int maxEnvelopes(int[][] envelopes) {
        Arrays.sort(envelopes, (a, b) -> a[0] == b[0] ? b[1] - a[1] : a[0] - b[0]);
        List<Integer> temp = new ArrayList<>();
        temp.add(envelopes[0][1]);
        for(int i=1; i<envelopes.length; i++){
            if(envelopes[i][1] > temp.get(temp.size()-1)){
                temp.add(envelopes[i][1]);
            }
            else{
                int ind = lowerBound(temp, envelopes[i][1]);
                temp.set(ind, envelopes[i][1]);
            }
        }
        return temp.size();
    }
    public int lowerBound(List<Integer> temp, int target){
        int low = 0;
        int high = temp.size()-1;
        int ans = temp.size();
        while(low <= high){
            int mid = low + (high-low)/2;
            if(temp.get(mid) >= target){
                ans = mid;
                high = mid-1;
            }
            else{
                low = mid+1;
            }
        }
        return ans;
    }
}
```
### Note:
- Here we use longest increasing subsequence by binary search to reduce T.C from O(n^2) to O(nlogn)
- We sort the envelopes by increasing order of widths and if two widths are same, we sort them by decreasing order of heights so that this code do not take two envelope with same width

