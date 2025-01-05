# [Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)
**Difficulty:** Easy

### Solution in Java
```java
class Solution {
    public String convertToTitle(int columnNumber) {
        StringBuilder sb = new StringBuilder();
        while(columnNumber-- > 0){
            sb.append((char)('A' + columnNumber%26));
            columnNumber /= 26;
        }
        return sb.reverse().toString();
    }
}
```
