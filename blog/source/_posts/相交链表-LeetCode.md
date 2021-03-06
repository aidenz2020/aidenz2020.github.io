---
title: 相交链表-LeetCode
date: 2020-09-11 21:08:32
tags:
 -链表
 -LeetCode
categories: 链表
---

# 相交链表-LeetCode

## link

https://leetcode-cn.com/problems/intersection-of-two-linked-lists/description/

## description

编写一个程序，找到两个单链表相交的起始节点。

如下面的两个链表：

![](https://raw.githubusercontent.com/aidenz2020/FigureBed/master/20200912083032.png)

在节点 c1 开始相交。

 

示例 1：

![](https://raw.githubusercontent.com/aidenz2020/FigureBed/master/20200912083143.png)

<!--more-->



输入：intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
输出：Reference of the node with value = 8
输入解释：相交节点的值为 8 （注意，如果两个链表相交则不能为 0）。从各自的表头开始算起，链表 A 为 [4,1,8,4,5]，链表 B 为 [5,0,1,8,4,5]。在 A 中，相交节点前有 2 个节点；在 B 中，相交节点前有 3 个节点。

示例 2：

![](https://raw.githubusercontent.com/aidenz2020/FigureBed/master/20200912083254.png)

输入：intersectVal = 2, listA = [0,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
输出：Reference of the node with value = 2
输入解释：相交节点的值为 2 （注意，如果两个链表相交则不能为 0）。从各自的表头开始算起，链表 A 为 [0,9,1,2,4]，链表 B 为 [3,2,4]。在 A 中，相交节点前有 3 个节点；在 B 中，相交节点前有 1 个节点。


示例 3：

![](https://raw.githubusercontent.com/aidenz2020/FigureBed/master/20200912083626.png)

输入：intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
输出：null
输入解释：从各自的表头开始算起，链表 A 为 [2,6,4]，链表 B 为 [1,5]。由于这两个链表不相交，所以 intersectVal 必须为 0，而 skipA 和 skipB 可以是任意值。
解释：这两个链表不相交，因此返回 null。


注意：

如果两个链表没有交点，返回 null.
在返回结果后，两个链表仍须保持原有的结构。
可假定整个链表结构中没有循环。
程序尽量满足 O(n) 时间复杂度，且仅用 O(1) 内存。

## solution

![](https://raw.githubusercontent.com/aidenz2020/FigureBed/master/20200912083032.png)

不难得出如果有公共的结点，则```len(a) + len(c) + len(b) = len(b) + len(c) + len(a)```

首先令两个遍历链表的指针同时指向两链表的头指针，之后每次两个指针同时向后遍历，如果a的指针遍历到链表尾部，则将指针指向b的头指针，遍历b的指针同理，第二次遍历如果有公共结点则两指针会同时指向第一个公共结点；如果没有公共结点，两指针则会同时指向空。



```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode l1 = headA,l2 = headB;
        while(l1 != l2) {
            l1 = l1 == null? headB : l1.next;
            l2 = l2 == null? headA : l2.next;
        }
        return l1;
    }
}
```



