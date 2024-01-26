---
title: 1921 Eliminate Maximum Number Of Monsters
summary: 1921 Eliminate Maximum Number Of Monsters LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1921 Eliminate Maximum Number Of Monsters LeetCode Solution Explained in all languages", "1921 Eliminate Maximum Number Of Monsters", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1921 Eliminate Maximum Number Of Monsters - Solution Explained/problem-solving.webp
    alt: 1921 Eliminate Maximum Number Of Monsters
    hiddenInList: true
    hiddenInSingle: false
---


# [1921. Eliminate Maximum Number of Monsters](https://leetcode.com/problems/eliminate-maximum-number-of-monsters)


## Description

<p>You are playing a video game where you are defending your city from a group of <code>n</code> monsters. You are given a <strong>0-indexed</strong> integer array <code>dist</code> of size <code>n</code>, where <code>dist[i]</code> is the <strong>initial distance</strong> in kilometers of the <code>i<sup>th</sup></code> monster from the city.</p>

<p>The monsters walk toward the city at a <strong>constant</strong> speed. The speed of each monster is given to you in an integer array <code>speed</code> of size <code>n</code>, where <code>speed[i]</code> is the speed of the <code>i<sup>th</sup></code> monster in kilometers per minute.</p>

<p>You have a weapon that, once fully charged, can eliminate a <strong>single</strong> monster. However, the weapon takes <strong>one minute</strong> to charge. The weapon is fully charged at the very start.</p>

<p>You lose when any monster reaches your city. If a monster reaches the city at the exact moment the weapon is fully charged, it counts as a <strong>loss</strong>, and the game ends before you can use your weapon.</p>

<p>Return <em>the <strong>maximum</strong> number of monsters that you can eliminate before you lose, or </em><code>n</code><em> if you can eliminate all the monsters before they reach the city.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> dist = [1,3,4], speed = [1,1,1]
<strong>Output:</strong> 3
<strong>Explanation:</strong>
In the beginning, the distances of the monsters are [1,3,4]. You eliminate the first monster.
After a minute, the distances of the monsters are [X,2,3]. You eliminate the second monster.
After a minute, the distances of the monsters are [X,X,2]. You eliminate the third monster.
All 3 monsters can be eliminated.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> dist = [1,1,2,3], speed = [1,1,1,1]
<strong>Output:</strong> 1
<strong>Explanation:</strong>
In the beginning, the distances of the monsters are [1,1,2,3]. You eliminate the first monster.
After a minute, the distances of the monsters are [X,0,1,2], so you lose.
You can only eliminate 1 monster.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> dist = [3,2,4], speed = [5,3,2]
<strong>Output:</strong> 1
<strong>Explanation:</strong>
In the beginning, the distances of the monsters are [3,2,4]. You eliminate the first monster.
After a minute, the distances of the monsters are [X,0,2], so you lose.
You can only eliminate 1 monster.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == dist.length == speed.length</code></li>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= dist[i], speed[i] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def eliminateMaximum(self, dist: List[int], speed: List[int]) -> int:
        times = sorted((d - 1) // s for d, s in zip(dist, speed))
        for i, t in enumerate(times):
            if t < i:
                return i
        return len(times)
```

```java
class Solution {
    public int eliminateMaximum(int[] dist, int[] speed) {
        int n = dist.length;
        int[] times = new int[n];
        for (int i = 0; i < n; ++i) {
            times[i] = (dist[i] - 1) / speed[i];
        }
        Arrays.sort(times);
        for (int i = 0; i < n; ++i) {
            if (times[i] < i) {
                return i;
            }
        }
        return n;
    }
}
```

```cpp
class Solution {
public:
    int eliminateMaximum(vector<int>& dist, vector<int>& speed) {
        int n = dist.size();
        vector<int> times;
        for (int i = 0; i < n; ++i) {
            times.push_back((dist[i] - 1) / speed[i]);
        }
        sort(times.begin(), times.end());
        for (int i = 0; i < n; ++i) {
            if (times[i] < i) {
                return i;
            }
        }
        return n;
    }
};
```

```go
func eliminateMaximum(dist []int, speed []int) int {
	n := len(dist)
	times := make([]int, n)
	for i, d := range dist {
		times[i] = (d - 1) / speed[i]
	}
	sort.Ints(times)
	for i, t := range times {
		if t < i {
			return i
		}
	}
	return n
}
```

```ts
function eliminateMaximum(dist: number[], speed: number[]): number {
    const n = dist.length;
    const times = new Array(n).fill(0);
    for (let i = 0; i < n; ++i) {
        times[i] = Math.floor((dist[i] - 1) / speed[i]);
    }
    times.sort((a, b) => a - b);
    for (let i = 0; i < n; ++i) {
        if (times[i] < i) {
            return i;
        }
    }
    return n;
}
```

```js
/**
 * @param {number[]} dist
 * @param {number[]} speed
 * @return {number}
 */
var eliminateMaximum = function (dist, speed) {
    let arr = [];
    for (let i = 0; i < dist.length; i++) {
        arr[i] = dist[i] / speed[i];
    }
    arr.sort((a, b) => a - b);
    let ans = 0;
    while (arr[0] > ans) {
        arr.shift();
        ++ans;
    }
    return ans;
};
```

```cs
public class Solution {
    public int EliminateMaximum(int[] dist, int[] speed) {
        int n = dist.Length;
        int[] times = new int[n];
        for (int i = 0; i < n; ++i) {
            times[i] = (dist[i] - 1) / speed[i];
        }
        Array.Sort(times);
        for (int i = 0; i < n; ++i) {
            if (times[i] < i) {
                return i;
            }
        }
        return n;
    }
}
```

<!-- tabs:end -->

<!-- end -->