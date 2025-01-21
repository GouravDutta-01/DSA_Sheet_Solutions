# [Missing And Repeating](https://www.geeksforgeeks.org/problems/find-missing-and-repeating2512/1)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    // Function to find two elements in array
    ArrayList<Integer> findTwoElement(int arr[]) {
        long n = arr.length;
        long sum = 0;
        long sum2 = 0;
        for(int val : arr){
            sum += val;
            sum2 += (long)val*val;
        }
        long diff = (long)n*(n+1)/2-sum;//(missing - repeating)
        long diff2 = (long)n*(n+1)*(2*n+1)/6-sum2;//(missing*missing - repeating*repeating)
        long add = (diff2/diff);//(missing+repeating)
        int missing = (int)((add+diff)/2);
        int repeating = (int)((add-diff)/2);
        ArrayList<Integer> ans = new ArrayList<>();
        ans.add(repeating);
        ans.add(missing);
        return ans;
    }
}
```