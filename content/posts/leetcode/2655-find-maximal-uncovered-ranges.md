---
title: 2655 Find Maximal Uncovered Ranges
summary: 2655 Find Maximal Uncovered Ranges LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2655 Find Maximal Uncovered Ranges LeetCode Solution Explained in all languages", "2655 Find Maximal Uncovered Ranges", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2655 Find Maximal Uncovered Ranges - Solution Explained/problem-solving.webp
    alt: 2655 Find Maximal Uncovered Ranges
    hiddenInList: true
    hiddenInSingle: false
---


# [2655. Find Maximal Uncovered Ranges](https://leetcode.com/problems/find-maximal-uncovered-ranges)


## Description

<p>You are given&nbsp;an integer <code>n</code>&nbsp;which is the length of a <strong>0-indexed</strong> array <code>nums</code>, and a <strong>0-indexed</strong> 2D-array <code>ranges</code>, which is a list of sub-ranges of <code>nums</code>&nbsp;(sub-ranges may <strong>overlap</strong>).</p>

<p>Each row <code>ranges[i]</code> has exactly 2 cells:</p>

<ul>
	<li><code>ranges[i][0]</code>, which shows the start of the i<sup>th</sup> range (inclusive)</li>
	<li><code>ranges[i][1]</code>, which shows the end of the i<sup>th</sup> range (inclusive)</li>
</ul>

<p>These ranges cover some cells of <code>nums</code>&nbsp;and leave&nbsp;some cells uncovered. Your task is to find all of the <b>uncovered </b>ranges with <strong>maximal</strong> length.</p>

<p>Return <em>a 2D-array </em><code>answer</code><em> of the uncovered ranges, <strong>sorted</strong> by the starting point in <strong>ascending order</strong>.</em></p>

<p>By all of the&nbsp;<strong>uncovered</strong> ranges with <strong>maximal</strong> length, we mean satisfying two conditions:</p>

<ul>
	<li>Each uncovered cell should belong to <strong>exactly</strong> one sub-range</li>
	<li>There should <strong>not exist</strong>&nbsp;two ranges (l<sub>1</sub>, r<sub>1</sub>) and (l<sub>2</sub>, r<sub>2</sub>) such that r<sub>1 </sub>+ 1 = l<sub>2</sub></li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 10, ranges = [[3,5],[7,8]]
<strong>Output:</strong> [[0,2],[6,6],[9,9]]
<strong>Explanation:</strong> The ranges (3, 5) and (7, 8) are covered, so if we simplify the array nums to a binary array where 0 shows an uncovered cell and 1 shows a covered cell, the array becomes [0,0,0,1,1,1,0,1,1,0] in which we can observe that the ranges (0, 2), (6, 6) and (9, 9) aren&#39;t covered.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 3, ranges = [[0,2]]
<strong>Output:</strong> []
<strong>Explanation: </strong>In this example, the whole of the array nums is covered and there are no uncovered cells so the output is an empty array.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 7, ranges = [[2,4],[0,3]]
<strong>Output:</strong> [[5,6]]
<strong>Explanation:</strong> The ranges (0, 3) and (2, 4) are covered, so if we simplify the array nums to a binary array where 0 shows an uncovered cell and 1 shows a covered cell, the array becomes [1,1,1,1,1,0,0] in which we can observe that the range (5, 6) is uncovered.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;=&nbsp;10<sup>9</sup></code></li>
	<li><code>0 &lt;= ranges.length &lt;= 10<sup>6</sup></code></li>
	<li><code>ranges[i].length = 2</code></li>
	<li><code>0 &lt;= ranges[i][j] &lt;= n - 1</code></li>
	<li><code>ranges[i][0] &lt;=&nbsp;ranges[i][1]</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def findMaximalUncoveredRanges(
        self, n: int, ranges: List[List[int]]
    ) -> List[List[int]]:
        ranges.sort()
        last = -1
        ans = []
        for l, r in ranges:
            if last + 1 < l:
                ans.append([last + 1, l - 1])
            last = max(last, r)
        if last + 1 < n:
            ans.append([last + 1, n - 1])
        return ans
```

```java
class Solution {
    public int[][] findMaximalUncoveredRanges(int n, int[][] ranges) {
        Arrays.sort(ranges, (a, b) -> a[0] - b[0]);
        int last = -1;
        List<int[]> ans = new ArrayList<>();
        for (int[] range : ranges) {
            int l = range[0], r = range[1];
            if (last + 1 < l) {
                ans.add(new int[] {last + 1, l - 1});
            }
            last = Math.max(last, r);
        }
        if (last + 1 < n) {
            ans.add(new int[] {last + 1, n - 1});
        }
        return ans.toArray(new int[0][]);
    }
}
```

```cpp
class Solution {
public:
    vector<vector<int>> findMaximalUncoveredRanges(int n, vector<vector<int>>& ranges) {
        sort(ranges.begin(), ranges.end(), [](const vector<int>& a, const vector<int>& b) {
            return a[0] < b[0];
        });
        int last = -1;
        vector<vector<int>> ans;
        for (auto& range : ranges) {
            int l = range[0], r = range[1];
            if (last + 1 < l) {
                ans.push_back({last + 1, l - 1});
            }
            last = max(last, r);
        }
        if (last + 1 < n) {
            ans.push_back({last + 1, n - 1});
        }
        return ans;
    }
};
```

```go
func findMaximalUncoveredRanges(n int, ranges [][]int) (ans [][]int) {
	sort.Slice(ranges, func(i, j int) bool { return ranges[i][0] < ranges[j][0] })
	last := -1
	for _, r := range ranges {
		if last+1 < r[0] {
			ans = append(ans, []int{last + 1, r[0] - 1})
		}
		last = max(last, r[1])
	}
	if last+1 < n {
		ans = append(ans, []int{last + 1, n - 1})
	}
	return
}
```

<!-- tabs:end -->

<!-- end -->