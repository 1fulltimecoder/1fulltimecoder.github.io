---
title: 1012 Numbers With Repeated Digits
summary: 1012 Numbers With Repeated Digits LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1012 Numbers With Repeated Digits LeetCode Solution Explained in all languages", "1012 Numbers With Repeated Digits", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1012 Numbers With Repeated Digits - Solution Explained/problem-solving.webp
    alt: 1012 Numbers With Repeated Digits
    hiddenInList: true
    hiddenInSingle: false
---


# [1012. Numbers With Repeated Digits](https://leetcode.com/problems/numbers-with-repeated-digits)


## Description

<p>Given an integer <code>n</code>, return <em>the number of positive integers in the range </em><code>[1, n]</code><em> that have <strong>at least one</strong> repeated digit</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 20
<strong>Output:</strong> 1
<strong>Explanation:</strong> The only positive number (&lt;= 20) with at least 1 repeated digit is 11.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 100
<strong>Output:</strong> 10
<strong>Explanation:</strong> The positive numbers (&lt;= 100) with atleast 1 repeated digit are 11, 22, 33, 44, 55, 66, 77, 88, 99, and 100.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 1000
<strong>Output:</strong> 262
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def numDupDigitsAtMostN(self, n: int) -> int:
        return n - self.f(n)

    def f(self, n):
        def A(m, n):
            return 1 if n == 0 else A(m, n - 1) * (m - n + 1)

        vis = [False] * 10
        ans = 0
        digits = [int(c) for c in str(n)[::-1]]
        m = len(digits)
        for i in range(1, m):
            ans += 9 * A(9, i - 1)
        for i in range(m - 1, -1, -1):
            v = digits[i]
            j = 1 if i == m - 1 else 0
            while j < v:
                if not vis[j]:
                    ans += A(10 - (m - i), i)
                j += 1
            if vis[v]:
                break
            vis[v] = True
            if i == 0:
                ans += 1
        return ans
```

```java
class Solution {
    public int numDupDigitsAtMostN(int n) {
        return n - f(n);
    }

    public int f(int n) {
        List<Integer> digits = new ArrayList<>();
        while (n != 0) {
            digits.add(n % 10);
            n /= 10;
        }
        int m = digits.size();
        int ans = 0;
        for (int i = 1; i < m; ++i) {
            ans += 9 * A(9, i - 1);
        }
        boolean[] vis = new boolean[10];
        for (int i = m - 1; i >= 0; --i) {
            int v = digits.get(i);
            for (int j = i == m - 1 ? 1 : 0; j < v; ++j) {
                if (vis[j]) {
                    continue;
                }
                ans += A(10 - (m - i), i);
            }
            if (vis[v]) {
                break;
            }
            vis[v] = true;
            if (i == 0) {
                ++ans;
            }
        }
        return ans;
    }

    private int A(int m, int n) {
        return n == 0 ? 1 : A(m, n - 1) * (m - n + 1);
    }
}
```

```cpp
class Solution {
public:
    int numDupDigitsAtMostN(int n) {
        return n - f(n);
    }

    int f(int n) {
        int ans = 0;
        vector<int> digits;
        while (n) {
            digits.push_back(n % 10);
            n /= 10;
        }
        int m = digits.size();
        vector<bool> vis(10);
        for (int i = 1; i < m; ++i) {
            ans += 9 * A(9, i - 1);
        }
        for (int i = m - 1; ~i; --i) {
            int v = digits[i];
            for (int j = i == m - 1 ? 1 : 0; j < v; ++j) {
                if (!vis[j]) {
                    ans += A(10 - (m - i), i);
                }
            }
            if (vis[v]) {
                break;
            }
            vis[v] = true;
            if (i == 0) {
                ++ans;
            }
        }
        return ans;
    }

    int A(int m, int n) {
        return n == 0 ? 1 : A(m, n - 1) * (m - n + 1);
    }
};
```

```go
func numDupDigitsAtMostN(n int) int {
	return n - f(n)
}

func f(n int) int {
	digits := []int{}
	for n != 0 {
		digits = append(digits, n%10)
		n /= 10
	}
	m := len(digits)
	vis := make([]bool, 10)
	ans := 0
	for i := 1; i < m; i++ {
		ans += 9 * A(9, i-1)
	}
	for i := m - 1; i >= 0; i-- {
		v := digits[i]
		j := 0
		if i == m-1 {
			j = 1
		}
		for ; j < v; j++ {
			if !vis[j] {
				ans += A(10-(m-i), i)
			}
		}
		if vis[v] {
			break
		}
		vis[v] = true
		if i == 0 {
			ans++
		}
	}
	return ans
}

func A(m, n int) int {
	if n == 0 {
		return 1
	}
	return A(m, n-1) * (m - n + 1)
}
```

```ts
function numDupDigitsAtMostN(n: number): number {
    return n - f(n);
}

function f(n: number): number {
    const nums: number[] = [];
    let i = -1;
    for (; n; n = Math.floor(n / 10)) {
        nums[++i] = n % 10;
    }
    const dp = Array.from({ length: 11 }, () => Array(1 << 11).fill(-1));
    const dfs = (pos: number, mask: number, lead: boolean, limit: boolean): number => {
        if (pos < 0) {
            return lead ? 0 : 1;
        }
        if (!lead && !limit && dp[pos][mask] !== -1) {
            return dp[pos][mask];
        }
        const up = limit ? nums[pos] : 9;
        let ans = 0;
        for (let i = 0; i <= up; ++i) {
            if ((mask >> i) & 1) {
                continue;
            }
            if (lead && i === 0) {
                ans += dfs(pos - 1, mask, lead, limit && i === up);
            } else {
                ans += dfs(pos - 1, mask | (1 << i), false, limit && i === up);
            }
        }
        if (!lead && !limit) {
            dp[pos][mask] = ans;
        }
        return ans;
    };
    return dfs(i, 0, true, true);
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def numDupDigitsAtMostN(self, n: int) -> int:
        return n - self.f(n)

    def f(self, n: int) -> int:
        @cache
        def dfs(pos: int, mask: int, lead: bool, limit: bool) -> int:
            if pos < 0:
                return int(lead) ^ 1
            up = nums[pos] if limit else 9
            ans = 0
            for i in range(up + 1):
                if mask >> i & 1:
                    continue
                if i == 0 and lead:
                    ans += dfs(pos - 1, mask, lead, limit and i == up)
                else:
                    ans += dfs(pos - 1, mask | 1 << i, False, limit and i == up)
            return ans

        nums = []
        while n:
            nums.append(n % 10)
            n //= 10
        return dfs(len(nums) - 1, 0, True, True)
```

```java
class Solution {
    private int[] nums = new int[11];
    private Integer[][] dp = new Integer[11][1 << 11];

    public int numDupDigitsAtMostN(int n) {
        return n - f(n);
    }

    private int f(int n) {
        int i = -1;
        for (; n > 0; n /= 10) {
            nums[++i] = n % 10;
        }
        return dfs(i, 0, true, true);
    }

    private int dfs(int pos, int mask, boolean lead, boolean limit) {
        if (pos < 0) {
            return lead ? 0 : 1;
        }
        if (!lead && !limit && dp[pos][mask] != null) {
            return dp[pos][mask];
        }
        int ans = 0;
        int up = limit ? nums[pos] : 9;
        for (int i = 0; i <= up; ++i) {
            if ((mask >> i & 1) == 1) {
                continue;
            }
            if (i == 0 && lead) {
                ans += dfs(pos - 1, mask, lead, limit && i == up);
            } else {
                ans += dfs(pos - 1, mask | 1 << i, false, limit && i == up);
            }
        }
        if (!lead && !limit) {
            dp[pos][mask] = ans;
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int numDupDigitsAtMostN(int n) {
        return n - f(n);
    }

private:
    int nums[11];
    int dp[11][1 << 11];

    int f(int n) {
        memset(dp, -1, sizeof(dp));
        int i = -1;
        for (; n; n /= 10) {
            nums[++i] = n % 10;
        }
        return dfs(i, 0, true, true);
    }

    int dfs(int pos, int mask, bool lead, bool limit) {
        if (pos < 0) {
            return lead ? 0 : 1;
        }
        if (!lead && !limit && dp[pos][mask] != -1) {
            return dp[pos][mask];
        }
        int up = limit ? nums[pos] : 9;
        int ans = 0;
        for (int i = 0; i <= up; ++i) {
            if (mask >> i & 1) {
                continue;
            }
            if (i == 0 && lead) {
                ans += dfs(pos - 1, mask, lead, limit && i == up);
            } else {
                ans += dfs(pos - 1, mask | 1 << i, false, limit && i == up);
            }
        }
        if (!lead && !limit) {
            dp[pos][mask] = ans;
        }
        return ans;
    }
};
```

```go
func numDupDigitsAtMostN(n int) int {
	return n - f(n)
}

func f(n int) int {
	nums := []int{}
	for ; n > 0; n /= 10 {
		nums = append(nums, n%10)
	}
	dp := [11][1 << 11]int{}
	for i := range dp {
		for j := range dp[i] {
			dp[i][j] = -1
		}
	}
	var dfs func(int, int, bool, bool) int
	dfs = func(pos int, mask int, lead bool, limit bool) int {
		if pos < 0 {
			if lead {
				return 0
			}
			return 1
		}
		if !lead && !limit && dp[pos][mask] != -1 {
			return dp[pos][mask]
		}
		up := 9
		if limit {
			up = nums[pos]
		}
		ans := 0
		for i := 0; i <= up; i++ {
			if mask>>i&1 == 1 {
				continue
			}
			if i == 0 && lead {
				ans += dfs(pos-1, mask, lead, limit && i == up)
			} else {
				ans += dfs(pos-1, mask|1<<i, false, limit && i == up)
			}
		}
		if !lead && !limit {
			dp[pos][mask] = ans
		}
		return ans
	}
	return dfs(len(nums)-1, 0, true, true)
}
```

<!-- tabs:end -->

<!-- end -->