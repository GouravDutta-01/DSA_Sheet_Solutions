# [Repeat and Missing Number Array](https://www.interviewbit.com/problems/repeat-and-missing-number-array/)
**Difficulty:** Medium

### Solution in Java
```java
public class Solution {
    public ArrayList<Integer> repeatedNumber(final List<Integer> A) {
        ArrayList<Integer> ans = new ArrayList<>();
        HashSet<Integer> set = new HashSet<>();
        for(int val : A){
            if(set.contains(val)){
                ans.add(val);
            }
            set.add(val);
        }
        for(int i=1; i<=A.size(); i++){
            if(!set.contains(i)){
                ans.add(i);
                break;
            }
        }
        return ans;
    }
}
```
