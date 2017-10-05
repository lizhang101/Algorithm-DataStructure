## [2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/description/) - medium

### Description
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
```

### Solution
```
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int carry = 0;  
        int sum = 0;
        ListNode dummy = new ListNode(0);
        ListNode prev = dummy;
        while (l1 != null || l2 != null || carry != 0) {
            sum = (l1 == null ? 0:l1.val) + (l2 == null ? 0:l2.val) + carry;
            carry = sum / 10;
            sum -= carry * 10;
            ListNode cur = new ListNode(sum);
            prev.next = cur;
            prev = cur;
            l1 = l1 == null ? l1:l1.next;
            l2 = l2 == null ? l2:l2.next;
        }
        return dummy.next;
    }
}
```

## [445. Add Two Numbers II](https://leetcode.com/problems/add-two-numbers-ii/description/) - medium

### Description
You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Follow up:**
What if you cannot modify the input lists? In other words, reversing the lists is not allowed.

Example:
```
Input: (7 -> 2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 8 -> 0 -> 7
```

### Solution
- reverse linkedlist, then add.
```
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        return add(reverseLL(l1), reverseLL(l2));
    }
    private ListNode reverseLL(ListNode l) {
        ListNode prev = null;
        ListNode cur = l;
        while (cur != null) {
            ListNode next = cur.next;
            cur.next = prev;
            prev = cur;
            cur = next;
        }
        return prev;
    }
    private ListNode add(ListNode l1, ListNode l2) {
        ListNode prev = null;
        ListNode cur = null;
        int carry = 0;
        while (l1 != null || l2 != null) {
            int sum = (l1 != null ? l1.val : 0) + (l2 != null ? l2.val : 0) + carry;
            carry = sum / 10;
            cur = new ListNode(sum%10);
            cur.next = prev;
            prev = cur; 
            l1 = l1 != null ? l1.next : l1;
            l2 = l2 != null ? l2.next : l2;
        }
        if (carry != 0)  {
            cur = new ListNode(carry);
            cur.next = prev;
        }
        return cur;
    }
}
```

- do not reverse linkedlist, use stack
```
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        Stack<Integer> s1 = new Stack();
        Stack<Integer> s2 = new Stack();
        ListNode prev = null;
        ListNode cur = null;
        int carry = 0;
        while (l1 != null)  {
            s1.push(l1.val);
            l1 = l1.next;
        }
        while (l2 != null) {
            s2.push(l2.val);
            l2 = l2.next;
        }
        while (!s1.empty() || !s2.empty()) {
            int sum = (s1.empty() ? 0 : s1.pop()) + (s2.empty() ? 0 : s2.pop()) + carry;
            carry = sum / 10;
            cur = new ListNode(sum%10);
            cur.next = prev;
            prev = cur;
        }
        if (carry != 0)  {
            cur = new ListNode(carry);
            cur.next = prev;
        }
        return cur;
    }
}
```

- do not reverse linkedlist, and do not use extra space. Recursion
```
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int len1 = calcLen(l1);
        int len2 = calcLen(l2);
        ListNode res = len1 > len2 ? l1 : l2;
        int carry = (len1 > len2 ? add(l1, l2, len1-len2) : add(l2, l1, len2-len1));
        if (carry > 0)  {
            ListNode head = new ListNode(carry);
            head.next = res;
            res = head;
        }
        return res;
    }
    private int add(ListNode n1, ListNode n2, int offset) {
        int sum = 0;
        if (offset > 0)  {
            sum = n1.val + add(n1.next, n2, offset-1);
        } else {
            if (n1 == null)    return 0;
            sum = n1.val + n2.val + add(n1.next, n2.next, 0);
        }
            
        n1.val = sum%10;
        return sum/10;
    }
    private int calcLen(ListNode l) {
        int len = 0;
        while (l != null) {
            ++len;
            l = l.next;
        }  
        return len;
    }
}
```

## [148. Sort List](https://leetcode.com/problems/sort-list/description/)

### Description
Sort a linked list in O(n log n) time using constant space complexity.

## [147. Insertion Sort List](https://leetcode.com/problems/insertion-sort-list/description/)

### Description
Sort a linked list using insertion sort.

## [143. Reorder List](https://leetcode.com/problems/reorder-list/description/)

### Description
Given a singly linked list L: L0?L1?…?Ln-1?Ln,
reorder it to: L0?Ln?L1?Ln-1?L2?Ln-2?…

You must do this in-place without altering the nodes' values.

For example,
Given `{1,2,3,4}`, reorder it to `{1,4,2,3}`.


