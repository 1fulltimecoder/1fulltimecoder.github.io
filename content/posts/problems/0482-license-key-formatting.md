---
title: 0482 License Key Formatting
summary: 0482 License Key Formatting LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0482-license-key-formatting LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0482 License Key Formatting - Solution Explained/problem-solving.webp
    alt: 0482 License Key Formatting
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/license-key-formatting/">482. License Key Formatting</a></h2><h3>Easy</h3><hr><div><p>You are given a license key represented as a string <code>s</code> that consists of only alphanumeric characters and dashes. The string is separated into <code>n + 1</code> groups by <code>n</code> dashes. You are also given an integer <code>k</code>.</p>

<p>We want to reformat the string <code>s</code> such that each group contains exactly <code>k</code> characters, except for the first group, which could be shorter than <code>k</code> but still must contain at least one character. Furthermore, there must be a dash inserted between two groups, and you should convert all lowercase letters to uppercase.</p>

<p>Return <em>the reformatted license key</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> s = "5F3Z-2e-9-w", k = 4
<strong>Output:</strong> "5F3Z-2E9W"
<strong>Explanation:</strong> The string s has been split into two parts, each part has 4 characters.
Note that the two extra dashes are not needed and can be removed.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> s = "2-5g-3-J", k = 2
<strong>Output:</strong> "2-5G-3J"
<strong>Explanation:</strong> The string s has been split into three parts, each part has 2 characters except the first part as it could be shorter as mentioned above.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of English letters, digits, and dashes <code>'-'</code>.</li>
	<li><code>1 &lt;= k &lt;= 10<sup>4</sup></code></li>
</ul>
</div>

---




```python
class Solution:
    def licenseKeyFormatting(self, s: str, k: int) -> str:
        s = s[::-1]
        res = ""
        tmp = ""
        for i in s:
            if i == '-': continue
            tmp += i.upper()
            if len(tmp) == k:
                res += tmp + '-'
                tmp = ""
        
        res += tmp
        if not res: return ""
        if res[-1] == "-": res = res[:-1]
        res = res[::-1]
        return res
```