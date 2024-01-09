---
title: 684 Redundant Connection
summary: 684 Redundant Connection LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
aliases: ["/posts/684-redundant-connection", "/blog/posts/684-redundant-connection", "/684-redundant-connection"]
keywords: LeetCode, leetcode solution in Python3 C++ Java, 684-redundant-connection solution
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_70_bold:684 Redundant Connection/problem-solving.webp
    alt: 684 Redundant Connection
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/redundant-connection/">684. Redundant Connection</a></h2><h3>Medium</h3><hr><div><p>In this problem, a tree is an <strong>undirected graph</strong> that is connected and has no cycles.</p>

<p>You are given a graph that started as a tree with <code>n</code> nodes labeled from <code>1</code> to <code>n</code>, with one additional edge added. The added edge has two <strong>different</strong> vertices chosen from <code>1</code> to <code>n</code>, and was not an edge that already existed. The graph is represented as an array <code>edges</code> of length <code>n</code> where <code>edges[i] = [a<sub>i</sub>, b<sub>i</sub>]</code> indicates that there is an edge between nodes <code>a<sub>i</sub></code> and <code>b<sub>i</sub></code> in the graph.</p>

<p>Return <em>an edge that can be removed so that the resulting graph is a tree of </em><code>n</code><em> nodes</em>. If there are multiple answers, return the answer that occurs last in the input.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/02/reduntant1-1-graph.jpg" style="width: 222px; height: 222px;">
<pre><strong>Input:</strong> edges = [[1,2],[1,3],[2,3]]
<strong>Output:</strong> [2,3]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/02/reduntant1-2-graph.jpg" style="width: 382px; height: 222px;">
<pre><strong>Input:</strong> edges = [[1,2],[2,3],[3,4],[1,4],[1,5]]
<strong>Output:</strong> [1,4]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == edges.length</code></li>
	<li><code>3 &lt;= n &lt;= 1000</code></li>
	<li><code>edges[i].length == 2</code></li>
	<li><code>1 &lt;= a<sub>i</sub> &lt; b<sub>i</sub> &lt;= edges.length</code></li>
	<li><code>a<sub>i</sub> != b<sub>i</sub></code></li>
	<li>There are no repeated edges.</li>
	<li>The given graph is connected.</li>
</ul>
</div>

---




```python
class Solution:
    def findRedundantConnection(self, edges: List[List[int]]) -> List[int]:
        parentDict = {i:i for i in range(len(edges)+1)}
        
        def find(node):
            while node != parentDict[node]:
                node = parentDict[node]
            return node
        
        def union(a, b):
            aRoot = find(a)
            bRoot = find(b)
            if aRoot == bRoot: return [a, b]
            parentDict[bRoot] = aRoot
        
        for a, b in edges:
            if union(a, b): return union(a, b)
        
        return -1
```