# [Find Beautiful Indices in the Given Array I](https://leetcode.com/problems/find-beautiful-indices-in-the-given-array-i/)
**Difficulty:** Easy

### Solution 1 in Java
```java
class Solution {
    public List<Integer> beautifulIndices(String s, String a, String b, int k) {
        List<Integer> aList = new ArrayList<>();
        List<Integer> bList = new ArrayList<>();
        for(int i=0; i<=s.length()-a.length(); i++){
            if(s.startsWith(a, i)){
                aList.add(i);
            }
        }
        for(int i=0; i<=s.length()-b.length(); i++){
            if(s.startsWith(b, i)){
                bList.add(i);
            }
        }
        List<Integer> ans = new ArrayList<>();
        for(int i : aList){
            for(int j : bList){
                if(Math.abs(j-i) <= k){
                    ans.add(i);
                    break;
                }
            }
        }
        return ans;
    }
}
```
### Solution 2 in Java
```java
class Solution {
    public List<Integer> beautifulIndices(String s, String a, String b, int k) {
        List<Integer> aList = kmp(s, a);
        List<Integer> bList = kmp(s, b);
        List<Integer> ans = new ArrayList<>();
        for(int i : aList){
            binarySearch(i-k, i+k, bList, ans);//adds i to ans if i is a beautiful index by using binary search
        }
        return ans; 
    }
    public void binarySearch(int from, int to, List<Integer> bList, List<Integer> ans){
        int low = 0;
        int high = bList.size()-1;
        while(low <= high){
            int mid = low + (high-low)/2;
            if(bList.get(mid) >= from && bList.get(mid) <= to){
                ans.add((from+to)/2);//adding the beautiful index
                return;
            }
            if(bList.get(mid) < from){
                low = mid+1;
            }
            else if(bList.get(mid) > to){
                high = mid-1;
            }   
        }
    }
    public List<Integer> kmp(String s, String p){
        String str = p + "#" + s;
        int[] lps = new int[str.length()];//lps[i] is the length of the longest proper prefix of the substring s[0...i] which is also a part of suffix of this substring
        int i = 1;
        int j = 0;
        while(i < str.length()){
            if(str.charAt(i) == str.charAt(j)){
                lps[i] = j+1;
                i++;
                j++;
            }
            else{
                while(j > 0 && str.charAt(i) != str.charAt(j)){
                    j = lps[j-1];
                }
                if(str.charAt(i) == str.charAt(j)){
                    lps[i] = j+1;
                    j++;
                }
                i++;
            }
        }
        List<Integer> list = new ArrayList<>();
        for(int k=p.length()+1; k<str.length(); k++){
            if(lps[k] == p.length()){
                list.add(k-p.length()-p.length());
            }
        }
        return list;
    }
}
```