# [K Sized Subarray Maximum](https://www.geeksforgeeks.org/problems/maximum-of-all-subarrays-of-size-k3101/1)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    // Function to find maximum of each subarray of size k.
    public ArrayList<Integer> max_of_subarrays(int arr[], int k) {
        ArrayList<Integer> ans = new ArrayList<>();
        Deque<Integer> dq = new LinkedList<>();
        for(int i=0; i<arr.length; i++){
            if(!dq.isEmpty() && dq.peekFirst() <= i-k){
                dq.pollFirst();//taking out elements that is outside window
            }
            while(!dq.isEmpty() && arr[dq.peekLast()] <= arr[i]){
                dq.pollLast();//maintaining a monotonic decreasing stack
            }
            dq.addLast(i);
            if(i >= k-1){
                ans.add(arr[dq.peekFirst()]);
                
            }
        }
        return ans;
    }
}
```
### Note:
- We maintain a monotonic decreasing stack so that if the current element from array we want to add in stack is greater than the current greatest value in top of stack, we remove the current greatest value from top of the stack and if current value to be added in stack is lesser than the greatest value present in top of stack, we still need to add it as it can be used in future window if needed.
