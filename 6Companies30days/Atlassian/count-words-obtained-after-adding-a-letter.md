# [Count Words Obtained After Adding a Letter](https://leetcode.com/problems/count-words-obtained-after-adding-a-letter/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int wordCount(String[] startWords, String[] targetWords) {
        HashSet<String> setStart = new HashSet<>();
        for(String s : startWords){
            char[] ch = s.toCharArray();
            Arrays.sort(ch);//sorting to help us tackle the problem of getting multiple permutations of rearranged string to compare
            setStart.add(new String(ch));
        }
        int count = 0;
        for(String s : targetWords){
            char[] ch = s.toCharArray();
            Arrays.sort(ch);
            String target = new String(ch);
            for(int i=0; i<target.length(); i++){//deleting single character and checking if remaining string is present in setStart or not
                StringBuilder sb = new StringBuilder(target);
                sb.deleteCharAt(i);
                if(setStart.contains(sb.toString())){
                    count++;
                    break;
                }
            }
        }
        return count;
    }
}
```
