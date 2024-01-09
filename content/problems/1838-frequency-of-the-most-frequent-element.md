---
title: 1838 Frequency Of The Most Frequent Element
summary: 1838 Frequency Of The Most Frequent Element LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
aliases: ["/posts/1838-frequency-of-the-most-frequent-element", "/blog/posts/1838-frequency-of-the-most-frequent-element", "/1838-frequency-of-the-most-frequent-element"]
keywords: LeetCode, leetcode solution in Python3 C++ Java, 1838-frequency-of-the-most-frequent-element solution
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_70_bold:1838 Frequency Of The Most Frequent Element/problem-solving.webp
    alt: 1838 Frequency Of The Most Frequent Element
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/frequency-of-the-most-frequent-element/">1838. Frequency of the Most Frequent Element</a></h2><h3>Medium</h3><hr><div><p>The <strong>frequency</strong> of an element is the number of times it occurs in an array.</p>

<p>You are given an integer array <code>nums</code> and an integer <code>k</code>. In one operation, you can choose an index of <code>nums</code> and increment the element at that index by <code>1</code>.</p>

<p>Return <em>the <strong>maximum possible frequency</strong> of an element after performing <strong>at most</strong> </em><code>k</code><em> operations</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,4], k = 5
<strong>Output:</strong> 3<strong>
Explanation:</strong> Increment the first element three times and the second element two times to make nums = [4,4,4].
4 has a frequency of 3.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1,4,8,13], k = 5
<strong>Output:</strong> 2
<strong>Explanation:</strong> There are multiple optimal solutions:
- Increment the first element three times to make nums = [4,4,8,13]. 4 has a frequency of 2.
- Increment the second element four times to make nums = [1,8,8,13]. 8 has a frequency of 2.
- Increment the third element five times to make nums = [1,4,13,13]. 13 has a frequency of 2.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [3,9,6], k = 2
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= k &lt;= 10<sup>5</sup></code></li>
</ul>
</div>

---




```python
class Solution:
    def maxFrequency(self, nums, k):
        nums.sort()
        prefixSum = []
        s = 0
        for i in nums:
            prefixSum.append(s)
            s += i
        res = 1
        l = 0
        for r in range(len(nums)):
            if nums[r]*(r-l) - (prefixSum[r] - prefixSum[l]) <= k:
                res = max(res, r-l+1)
            else:
                l += 1
        print(prefixSum)
        return res
```