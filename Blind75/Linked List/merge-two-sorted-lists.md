# [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)
**Difficulty:** Easy

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
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummyHead = new ListNode(-1);
        ListNode temp = dummyHead;
        ListNode temp1 = list1;
        ListNode temp2 = list2;
        while(temp1 != null && temp2 != null){
            if(temp1.val <= temp2.val){
                temp.next = temp1;
                temp = temp.next;
                temp1 = temp1.next;
            }
            else{
                temp.next = temp2;
                temp = temp.next;
                temp2 = temp2.next;
            }
        }
        while(temp1 != null){
            temp.next = temp1;
            temp = temp.next;
            temp1 = temp1.next;
        }
        while(temp2 != null){
            temp.next = temp2;
            temp = temp.next;
            temp2 = temp2.next;
        }
        return dummyHead.next;
    }
}
```
