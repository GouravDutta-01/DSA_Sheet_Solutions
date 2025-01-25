# [Integer to English Words](https://leetcode.com/problems/integer-to-english-words/)
**Difficulty:** Hard

### Solution in Java
```java
class Solution {
    public String numberToWords(int num) {
        if(num == 0){
            return "Zero";
        }
        HashMap<Integer, String> map1 = new HashMap<>();
        under10(map1);
        HashMap<Integer, String> map2 = new HashMap<>();
        under20(map2);
        HashMap<Integer, String> map3 = new HashMap<>();
        under100(map3);
        return solve(num, map1, map2, map3);
    }
    public String solve(int num, HashMap<Integer, String> map1, HashMap<Integer, String> map2, HashMap<Integer, String> map3){
        if(num < 10){
            return map1.get(num);
        }
        if(num < 20){
            return map2.get(num);
        }
        if(num < 100){
            String s = map3.get(num/10);
            if(num%10 != 0){
                s += " " + map1.get(num%10);
            }
            return s;
        }
        if(num < 1000){
            String s = solve(num/100, map1, map2, map3) + " Hundred";
            if(num%100 != 0){
                s += " " + solve(num%100, map1, map2, map3);
            }
            return s;
        }
        if(num < 1000000){
            String s = solve(num/1000, map1, map2, map3) + " Thousand";
            if(num%1000 != 0){
                s += " " + solve(num%1000, map1, map2, map3);
            }
            return s;
        }
        if(num < (int)1e9){
            String s = solve(num/1000000, map1, map2, map3) + " Million";
            if(num%1000000 != 0){
                s += " " + solve(num%1000000, map1, map2, map3);
            }
            return s;
        }
        String s = solve(num/(int)1e9, map1, map2, map3) + " Billion";
        if(num%(int)1e9 != 0){
            s += " " + solve(num%(int)1e9, map1, map2, map3);
        }
        return s;
    }
    public void under10(HashMap<Integer, String> map){
        map.put(0, "");
        map.put(1, "One");
        map.put(2, "Two");
        map.put(3, "Three");
        map.put(4, "Four");
        map.put(5, "Five");
        map.put(6, "Six");
        map.put(7, "Seven");
        map.put(8, "Eight");
        map.put(9, "Nine");
    }
    public void under20(HashMap<Integer, String> map){
        map.put(10, "Ten");
        map.put(11, "Eleven");
        map.put(12, "Twelve");
        map.put(13, "Thirteen");
        map.put(14, "Fourteen");
        map.put(15, "Fifteen");
        map.put(16, "Sixteen");
        map.put(17, "Seventeen");
        map.put(18, "Eighteen");
        map.put(19, "Nineteen");
    }
    public void under100(HashMap<Integer, String> map){
        map.put(2, "Twenty");
        map.put(3, "Thirty");
        map.put(4, "Forty");
        map.put(5, "Fifty");
        map.put(6, "Sixty");
        map.put(7, "Seventy");
        map.put(8, "Eighty");
        map.put(9, "Ninety");
    }
}
```

