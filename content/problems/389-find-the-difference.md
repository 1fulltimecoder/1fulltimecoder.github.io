---
title: 389 Find The Difference
summary: 389 Find The Difference LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
aliases: ["/posts/389-find-the-difference", "/blog/posts/389-find-the-difference", "/389-find-the-difference"]
keywords: LeetCode, leetcode solution in Python3 C++ Java, 389-find-the-difference solution
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_70_bold:389 Find The Difference/problem-solving.webp
    alt: 389 Find The Difference
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/find-the-difference/">389. Find the Difference</a></h2><h3>Easy</h3><hr><div><p>You are given two strings <code>s</code> and <code>t</code>.</p>

<p>String <code>t</code> is generated by random shuffling string <code>s</code> and then add one more letter at a random position.</p>

<p>Return the letter that was added to <code>t</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "abcd", t = "abcde"
<strong>Output:</strong> "e"
<strong>Explanation:</strong> 'e' is the letter that was added.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "", t = "y"
<strong>Output:</strong> "y"
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 1000</code></li>
	<li><code>t.length == s.length + 1</code></li>
	<li><code>s</code> and <code>t</code> consist of lowercase English letters.</li>
</ul>
</div>

---




```python
class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        ds = {}
        for i in s:
            if i not in ds:
                ds[i] = 1
            else:
                ds[i] += 1
        
        dt = {}
        for i in t:
            if i not in dt:
                dt[i] = 1
            else:
                dt[i] += 1
        
        for i in dt:
            if i not in ds: return i
            else:
                if dt[i] > ds[i]: return i
```