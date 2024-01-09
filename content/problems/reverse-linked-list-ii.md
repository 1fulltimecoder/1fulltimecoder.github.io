---
title: Reverse Linked List Ii
summary: Reverse Linked List Ii LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
aliases: ["/posts/reverse-linked-list-ii", "/blog/posts/reverse-linked-list-ii", "/reverse-linked-list-ii"]
keywords: LeetCode, leetcode solution in Python3 C++ Java, reverse-linked-list-ii solution
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_70_bold:Reverse Linked List Ii/problem-solving.webp
    alt: Reverse Linked List Ii
    hiddenInList: true
    hiddenInSingle: false
---


<h2>92. Reverse Linked List II</h2><h3>Medium</h3><hr><div><p>Reverse a linked list from position <em>m</em> to <em>n</em>. Do it in one-pass.</p>

<p><strong>Note:&nbsp;</strong>1 ≤ <em>m</em> ≤ <em>n</em> ≤ length of list.</p>

<p><strong>Example:</strong></p>

<pre><strong>Input:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL, <em>m</em> = 2, <em>n</em> = 4
<strong>Output:</strong> 1-&gt;4-&gt;3-&gt;2-&gt;5-&gt;NULL
</pre>
</div>

---




```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseBetween(ListNode* head, int m, int n) {
        if (head == NULL) {
            return NULL;
        }
        ListNode* prev=NULL;
        ListNode* t=head;
        while(m>1){
            prev=t;
            t=t->next;
            m--;
            n--;
        }
        ListNode* c1=t;
        ListNode* p1=prev;
        ListNode* t1=NULL;
        while(n>0){
            t1=t->next;
            t->next=prev;
            prev=t;
            t=t1;
            n--;
        }
       if(p1!=NULL)
           p1->next=prev;
        else
            head=prev;
        c1->next=t;
        return head;
    }
};

```