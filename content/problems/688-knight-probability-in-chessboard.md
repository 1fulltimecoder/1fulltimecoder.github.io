---
title: 688 Knight Probability In Chessboard
summary: 688 Knight Probability In Chessboard LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
aliases: ["/posts/688-knight-probability-in-chessboard", "/blog/posts/688-knight-probability-in-chessboard", "/688-knight-probability-in-chessboard"]
keywords: LeetCode, leetcode solution in Python3 C++ Java, 688-knight-probability-in-chessboard solution
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_70_bold:688 Knight Probability In Chessboard/problem-solving.webp
    alt: 688 Knight Probability In Chessboard
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/knight-probability-in-chessboard/">688. Knight Probability in Chessboard</a></h2><h3>Medium</h3><hr><div><p>On an <code>n x n</code> chessboard, a knight starts at the cell <code>(row, column)</code> and attempts to make exactly <code>k</code> moves. The rows and columns are <strong>0-indexed</strong>, so the top-left cell is <code>(0, 0)</code>, and the bottom-right cell is <code>(n - 1, n - 1)</code>.</p>

<p>A chess knight has eight possible moves it can make, as illustrated below. Each move is two cells in a cardinal direction, then one cell in an orthogonal direction.</p>
<img src="https://assets.leetcode.com/uploads/2018/10/12/knight.png" style="width: 300px; height: 300px;">
<p>Each time the knight is to move, it chooses one of eight possible moves uniformly at random (even if the piece would go off the chessboard) and moves there.</p>

<p>The knight continues moving until it has made exactly <code>k</code> moves or has moved off the chessboard.</p>

<p>Return <em>the probability that the knight remains on the board after it has stopped moving</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> n = 3, k = 2, row = 0, column = 0
<strong>Output:</strong> 0.06250
<strong>Explanation:</strong> There are two moves (to (1,2), (2,1)) that will keep the knight on the board.
From each of those positions, there are also two moves that will keep the knight on the board.
The total probability the knight stays on the board is 0.0625.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 1, k = 0, row = 0, column = 0
<strong>Output:</strong> 1.00000
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 25</code></li>
	<li><code>0 &lt;= k &lt;= 100</code></li>
	<li><code>0 &lt;= row, column &lt;= n</code></li>
</ul>
</div>

---




```python
class Solution:
    def knightProbability(self, n: int, k: int, row: int, column: int) -> float:
        move = [[2,1],[2,-1],[-2,1],[-2,-1],[1,2],[1,-2],[-1,2],[-1,-2]] 
        memo = {}
        def solve(r, c, k):
            if not 0 <= r < n or not 0 <= c < n: return 0
            if k == 0: return 1
            key = (r, c, k)
            if key in memo:
                return memo[key]
            tmp = 0
            for m in move:
                i = r + m[0]
                j = c + m[1]
                tmp += solve(i,  j, k-1)
            memo[key] = tmp / 8
            return memo[key]
        
        return solve(row, column, k)
```