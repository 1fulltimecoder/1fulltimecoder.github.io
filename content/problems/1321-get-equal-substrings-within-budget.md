---
title: 1321 Get Equal Substrings Within Budget
summary: 1321 Get Equal Substrings Within Budget LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
aliases: ["/posts/1321-get-equal-substrings-within-budget", "/blog/posts/1321-get-equal-substrings-within-budget", "/1321-get-equal-substrings-within-budget"]
keywords: LeetCode, leetcode solution in Python3 C++ Java, 1321-get-equal-substrings-within-budget solution
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_70_bold:1321 Get Equal Substrings Within Budget/problem-solving.webp
    alt: 1321 Get Equal Substrings Within Budget
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/get-equal-substrings-within-budget">1321. Get Equal Substrings Within Budget</a></h2><h3>Medium</h3><hr><p>You are given two strings <code>s</code> and <code>t</code> of the same length and an integer <code>maxCost</code>.</p>

<p>You want to change <code>s</code> to <code>t</code>. Changing the <code>i<sup>th</sup></code> character of <code>s</code> to <code>i<sup>th</sup></code> character of <code>t</code> costs <code>|s[i] - t[i]|</code> (i.e., the absolute difference between the ASCII values of the characters).</p>

<p>Return <em>the maximum length of a substring of </em><code>s</code><em> that can be changed to be the same as the corresponding substring of </em><code>t</code><em> with a cost less than or equal to </em><code>maxCost</code>. If there is no substring from <code>s</code> that can be changed to its corresponding substring from <code>t</code>, return <code>0</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcd&quot;, t = &quot;bcdf&quot;, maxCost = 3
<strong>Output:</strong> 3
<strong>Explanation:</strong> &quot;abc&quot; of s can change to &quot;bcd&quot;.
That costs 3, so the maximum length is 3.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcd&quot;, t = &quot;cdef&quot;, maxCost = 3
<strong>Output:</strong> 1
<strong>Explanation:</strong> Each character in s costs 2 to change to character in t,  so the maximum length is 1.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcd&quot;, t = &quot;acde&quot;, maxCost = 0
<strong>Output:</strong> 1
<strong>Explanation:</strong> You cannot make any change, so the maximum length is 1.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>t.length == s.length</code></li>
	<li><code>0 &lt;= maxCost &lt;= 10<sup>6</sup></code></li>
	<li><code>s</code> and <code>t</code> consist of only lowercase English letters.</li>
</ul>


---




```python
class Solution:
    def equalSubstring(self, s: str, t: str, maxCost: int) -> int:
        arr = []
        for i in range(len(s)):
            d = abs(ord(s[i]) - ord(t[i]))
            arr.append(d)
        
        l = res = curSum = 0
        for r in range(len(s)):
            curSum += arr[r]
            while curSum > maxCost:
                curSum -= arr[l]
                l += 1
            res = max(res, r-l+1)
        
        return res
```