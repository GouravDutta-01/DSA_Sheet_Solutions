# [Encode and Decode Strings](https://www.geeksforgeeks.org/problems/encode-and-decode-strings/1)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {

    public String encode(String s[]) {
        StringBuilder sb = new StringBuilder();
        for(String str : s){
            sb.append(str.length() + "#" + str);
        }
        return sb.toString();
    }

    public String[] decode(String s) {
        ArrayList<String> list = new ArrayList<>();
        int i = 0;
        while(i < s.length()){
            int j = i;
            while(s.charAt(j) != '#'){
                j++;
            }
            int len = Integer.parseInt(s.substring(i, j));
            list.add(s.substring(j+1, j+1+len));
            i = j+1+len;
        }
        String[] ans = new String[list.size()];
        for(int k=0; k<list.size(); k++){
            ans[k] = list.get(k);
        }
        return ans;
    }
}
```
