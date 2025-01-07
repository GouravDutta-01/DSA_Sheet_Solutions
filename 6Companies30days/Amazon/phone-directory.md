# [Phone directory](https://www.geeksforgeeks.org/problems/phone-directory4628/1)
**Difficulty:** Hard

### Solution 1 in Java
```java
class Solution{
    static ArrayList<ArrayList<String>> displayContacts(int n, String contact[], String s){
        ArrayList<ArrayList<String>> ans = new ArrayList<>();
        StringBuilder sb = new StringBuilder();
        TreeSet<String> set = new TreeSet<>(Arrays.asList(contact));
        for(int i=0; i<s.length(); i++){
            char ch = s.charAt(i);
            sb.append(ch);
            ans.add(new ArrayList<>());
            for(String str : set){
                if(str.indexOf(sb.toString()) == 0){
                    ans.get(i).add(str);
                }
            }
            if(ans.get(i).size() == 0){
                ans.get(i).add("0");
            }
        }
        return ans;
    }
}
```
