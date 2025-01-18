# [Reorder List](https://leetcode.com/problems/reorder-list/)
**Difficulty:** Medium

### Solution in Java
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public void reorderList(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while(fast != null && fast.next != null){
            slow = slow.next;
            fast = fast.next.next;
        }
        ListNode revHead = reverseLL(slow);//dividing the LL into two halves and reversing the later half
        ListNode start = head;
        while(revHead.next != null){
            ListNode startNext = start.next;
            ListNode revNext = revHead.next;
            start.next = revHead;
            revHead.next = startNext;
            revHead = revNext;
            start = startNext;
        }   
    }
    public ListNode reverseLL(ListNode head){
        ListNode prev = null;
        ListNode curr = head;
        while(curr != null){
            ListNode temp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = temp;
        }
        return prev;
    }
}
```
