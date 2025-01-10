# [Group Anagrams](https://leetcode.com/problems/group-anagrams/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        int n = strs.length;
        List<List<String>> ans = new ArrayList<>();
        boolean[] vis = new boolean[n];
        for(int i=0; i<n; i++){
            if(vis[i]){
                continue;
            }
            List<String> curr = new ArrayList<>();
            curr.add(strs[i]);
            vis[i] = true;
            for(int j=i+1; j<n; j++){
                if(isAnagram(strs[i], strs[j])){
                    curr.add(strs[j]);
                    vis[j] = true;
                }
            }
            if(!curr.isEmpty()){
                ans.add(curr);
            }
        }
        return ans;
    }
    public boolean isAnagram(String s, String t) {
        if(s.length() != t.length()){
            return false;
        }
        int[] freq = new int[26];
        for(int i=0; i<s.length(); i++){
            freq[s.charAt(i)-'a']++;
            freq[t.charAt(i)-'a']--;
        }
        for(int i=0; i<26; i++){
            if(freq[i] != 0){
                return false;
            }
        }
        return true;
    }
}
```
