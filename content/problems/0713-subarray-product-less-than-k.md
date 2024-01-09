---
title: 0713 Subarray Product Less Than K
summary: 0713 Subarray Product Less Than K LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
aliases: ["/posts/0713-subarray-product-less-than-k", "/blog/posts/0713-subarray-product-less-than-k", "/0713-subarray-product-less-than-k"]
keywords: LeetCode, leetcode solution in Python3 C++ Java, 0713-subarray-product-less-than-k solution
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_70_bold:0713 Subarray Product Less Than K/problem-solving.webp
    alt: 0713 Subarray Product Less Than K
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/subarray-product-less-than-k/">713. Subarray Product Less Than K</a></h2><h3>Medium</h3><hr><div><p>Given an array of integers <code>nums</code> and an integer <code>k</code>, return <em>the number of contiguous subarrays where the product of all the elements in the subarray is strictly less than </em><code>k</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [10,5,2,6], k = 100
<strong>Output:</strong> 8
<strong>Explanation:</strong> The 8 subarrays that have product less than 100 are:
[10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6]
Note that [10, 5, 2] is not included as the product of 100 is not strictly less than k.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,3], k = 0
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 1000</code></li>
	<li><code>0 &lt;= k &lt;= 10<sup>6</sup></code></li>
</ul>
</div>

---




```python
class Solution:
    def numSubarrayProductLessThanK(self, nums: List[int], k: int) -> int:
        mul = 1
        l = 0
        res = 0
        for r in range(len(nums)):
            mul *= nums[r]
            while l <= r and mul >= k:
                mul //= nums[l]
                l += 1
            res += r-l+1
        return res
```