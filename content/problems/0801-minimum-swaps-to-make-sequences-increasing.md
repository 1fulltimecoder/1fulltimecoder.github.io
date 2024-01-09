---
title: 0801 Minimum Swaps To Make Sequences Increasing
summary: 0801 Minimum Swaps To Make Sequences Increasing LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
aliases: ["/posts/0801-minimum-swaps-to-make-sequences-increasing", "/blog/posts/0801-minimum-swaps-to-make-sequences-increasing", "/0801-minimum-swaps-to-make-sequences-increasing"]
keywords: LeetCode, leetcode solution in Python3 C++ Java, 0801-minimum-swaps-to-make-sequences-increasing solution
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_70_bold:0801 Minimum Swaps To Make Sequences Increasing/problem-solving.webp
    alt: 0801 Minimum Swaps To Make Sequences Increasing
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/minimum-swaps-to-make-sequences-increasing/">801. Minimum Swaps To Make Sequences Increasing</a></h2><h3>Hard</h3><hr><div><p>You are given two integer arrays of the same length <code>nums1</code> and <code>nums2</code>. In one operation, you are allowed to swap <code>nums1[i]</code> with <code>nums2[i]</code>.</p>

<ul>
	<li>For example, if <code>nums1 = [1,2,3,<u>8</u>]</code>, and <code>nums2 = [5,6,7,<u>4</u>]</code>, you can swap the element at <code>i = 3</code> to obtain <code>nums1 = [1,2,3,4]</code> and <code>nums2 = [5,6,7,8]</code>.</li>
</ul>

<p>Return <em>the minimum number of needed operations to make </em><code>nums1</code><em> and </em><code>nums2</code><em> <strong>strictly increasing</strong></em>. The test cases are generated so that the given input always makes it possible.</p>

<p>An array <code>arr</code> is <strong>strictly increasing</strong> if and only if <code>arr[0] &lt; arr[1] &lt; arr[2] &lt; ... &lt; arr[arr.length - 1]</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> nums1 = [1,3,5,4], nums2 = [1,2,3,7]
<strong>Output:</strong> 1
<strong>Explanation:</strong> 
Swap nums1[3] and nums2[3]. Then the sequences are:
nums1 = [1, 3, 5, 7] and nums2 = [1, 2, 3, 4]
which are both strictly increasing.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> nums1 = [0,3,5,8,9], nums2 = [2,1,4,6,9]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums1.length &lt;= 10<sup>5</sup></code></li>
	<li><code>nums2.length == nums1.length</code></li>
	<li><code>0 &lt;= nums1[i], nums2[i] &lt;= 2 * 10<sup>5</sup></code></li>
</ul>
</div>

---




```python
class Solution:
    def minSwap(self, nums1: List[int], nums2: List[int]) -> int:
        dp = [[-1]*2 for _ in range(len(nums1)+1)]
        def solve(prev1, prev2, i, swaped):
            if i >= len(nums1): return 0
            if dp[i][swaped] != -1: return dp[i][swaped] 
            ans = 2**31
            if nums1[i] > prev1 and nums2[i] > prev2:
                ans = min(ans, solve(nums1[i], nums2[i], i+1, 0))
            if nums1[i] > prev2 and nums2[i] > prev1:
                ans = min(ans, 1 + solve(nums2[i], nums1[i], i+1, 1))
            dp[i][swaped] = ans
            return ans
        
        return solve(-2**31, -2**31, 0, 0)
```