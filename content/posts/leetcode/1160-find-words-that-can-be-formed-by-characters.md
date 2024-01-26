---
title: 1160 Find Words That Can Be Formed By Characters
summary: 1160 Find Words That Can Be Formed By Characters LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1160 Find Words That Can Be Formed By Characters LeetCode Solution Explained in all languages", "1160 Find Words That Can Be Formed By Characters", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1160 Find Words That Can Be Formed By Characters - Solution Explained/problem-solving.webp
    alt: 1160 Find Words That Can Be Formed By Characters
    hiddenInList: true
    hiddenInSingle: false
---


# [1160. Find Words That Can Be Formed by Characters](https://leetcode.com/problems/find-words-that-can-be-formed-by-characters)


## Description

<p>You are given an array of strings <code>words</code> and a string <code>chars</code>.</p>

<p>A string is <strong>good</strong> if it can be formed by characters from <code>chars</code> (each character can only be used once).</p>

<p>Return <em>the sum of lengths of all good strings in words</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;cat&quot;,&quot;bt&quot;,&quot;hat&quot;,&quot;tree&quot;], chars = &quot;atach&quot;
<strong>Output:</strong> 6
<strong>Explanation:</strong> The strings that can be formed are &quot;cat&quot; and &quot;hat&quot; so the answer is 3 + 3 = 6.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;hello&quot;,&quot;world&quot;,&quot;leetcode&quot;], chars = &quot;welldonehoneyr&quot;
<strong>Output:</strong> 10
<strong>Explanation:</strong> The strings that can be formed are &quot;hello&quot; and &quot;world&quot; so the answer is 5 + 5 = 10.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= words.length &lt;= 1000</code></li>
	<li><code>1 &lt;= words[i].length, chars.length &lt;= 100</code></li>
	<li><code>words[i]</code> and <code>chars</code> consist of lowercase English letters.</li>
</ul>

## Solutions

### Solution 1: Counting

We can use an array $cnt$ of length $26$ to count the occurrence of each letter in the string $chars$.

Then we traverse the string array $words$. For each string $w$, we use an array $wc$ of length $26$ to count the occurrence of each letter in the string $w$. If for each letter $c$, $wc[c] \leq cnt[c]$, then we can spell the string $w$ with the letters in $chars$, otherwise we cannot spell the string $w$. If we can spell the string $w$, then we add the length of the string $w$ to the answer.

After the traversal, we can get the answer.

The time complexity is $O(L)$, and the space complexity is $O(C)$. Here, $L$ is the sum of the lengths of all strings in the problem, and $C$ is the size of the character set. In this problem, $C = 26$.

<!-- tabs:start -->

```python
class Solution:
    def countCharacters(self, words: List[str], chars: str) -> int:
        cnt = Counter(chars)
        ans = 0
        for w in words:
            wc = Counter(w)
            if all(cnt[c] >= v for c, v in wc.items()):
                ans += len(w)
        return ans
```

```java
class Solution {
    public int countCharacters(String[] words, String chars) {
        int[] cnt = new int[26];
        for (int i = 0; i < chars.length(); ++i) {
            ++cnt[chars.charAt(i) - 'a'];
        }
        int ans = 0;
        for (String w : words) {
            int[] wc = new int[26];
            boolean ok = true;
            for (int i = 0; i < w.length(); ++i) {
                int j = w.charAt(i) - 'a';
                if (++wc[j] > cnt[j]) {
                    ok = false;
                    break;
                }
            }
            if (ok) {
                ans += w.length();
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int countCharacters(vector<string>& words, string chars) {
        int cnt[26]{};
        for (char& c : chars) {
            ++cnt[c - 'a'];
        }
        int ans = 0;
        for (auto& w : words) {
            int wc[26]{};
            bool ok = true;
            for (auto& c : w) {
                int i = c - 'a';
                if (++wc[i] > cnt[i]) {
                    ok = false;
                    break;
                }
            }
            if (ok) {
                ans += w.size();
            }
        }
        return ans;
    }
};
```

```go
func countCharacters(words []string, chars string) (ans int) {
	cnt := [26]int{}
	for _, c := range chars {
		cnt[c-'a']++
	}
	for _, w := range words {
		wc := [26]int{}
		ok := true
		for _, c := range w {
			c -= 'a'
			wc[c]++
			if wc[c] > cnt[c] {
				ok = false
				break
			}
		}
		if ok {
			ans += len(w)
		}
	}
	return
}
```

```ts
function countCharacters(words: string[], chars: string): number {
    const idx = (c: string) => c.charCodeAt(0) - 'a'.charCodeAt(0);
    const cnt = new Array(26).fill(0);
    for (const c of chars) {
        cnt[idx(c)]++;
    }
    let ans = 0;
    for (const w of words) {
        const wc = new Array(26).fill(0);
        let ok = true;
        for (const c of w) {
            if (++wc[idx(c)] > cnt[idx(c)]) {
                ok = false;
                break;
            }
        }
        if (ok) {
            ans += w.length;
        }
    }
    return ans;
}
```

```php
class Solution {
    /**
     * @param String[] $words
     * @param String $chars
     * @return Integer
     */
    function countCharacters($words, $chars) {
        $sum = 0;
        for ($i = 0; $i < strlen($chars); $i++) {
            $hashtable[$chars[$i]] += 1;
        }
        for ($j = 0; $j < count($words); $j++) {
            $tmp = $hashtable;
            $sum += strlen($words[$j]);
            for ($k = 0; $k < strlen($words[$j]); $k++) {
                if (!isset($tmp[$words[$j][$k]]) || $tmp[$words[$j][$k]] === 0) {
                    $sum -= strlen($words[$j]);
                    break;
                }
                $tmp[$words[$j][$k]] -= 1;
            }
        }
        return $sum;
    }
}
```

<!-- tabs:end -->

<!-- end -->