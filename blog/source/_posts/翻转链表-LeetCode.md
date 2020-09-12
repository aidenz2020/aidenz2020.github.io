---
title: 翻转链表-LeetCode
date: 2020-09-12 17:01:51
tags:
 -LeetCode
 -链表
categories: 链表
---

# 翻转链表-LeetCode

## link

https://leetcode-cn.com/problems/reverse-linked-list/

## description

示例:

输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
进阶:
你可以迭代或递归地反转链表。你能否用两种方法解决这道题？

## solution

解法一：迭代法

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
    if (head == null || head.next == null) {
        return head;
    }
    ListNode next = head.next;
    ListNode newHead = reverseList(next);
    next.next = head;
    head.next = null;
    return newHead;
}

    
}
```

解法二： 头插法

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode l = null;
        while(head != null) {
            ListNode next = head.next;
            head.next = l;
            l = head;
            head = next;  
        }
        return l;
    }
}

    

```

