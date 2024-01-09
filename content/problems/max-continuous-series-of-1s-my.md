---
title: Max Continuous Series Of 1S My
summary: Max Continuous Series Of 1S My - Interviewbit Solution Explained
date: 2020-06-20
tags: [interviewbit]
series: [interviewbit]
keywords: [interviewbit, interviewbit solution in Python3 C++ Java, Max Continuous Series Of 1S My solution]
aliases: ["/posts/max-continuous-series-of-1s-my", "/blog/posts/max-continuous-series-of-1s-my", "/max-continuous-series-of-1s-my"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_70_bold:Max Continuous Series Of 1S My - Solution Explained/problem-solving.webp
    alt: Max Continuous Series Of 1S My
    hiddenInList: true
    hiddenInSingle: false
---

# Max Continuous Series Of 1s My

https://www.interviewbit.com/problems/max-continuous-series-of-1s-my


## Solution

```cpp
vector<int> Solution::maxone(vector<int> &arr, int m) {

    int n = arr.size();
    int i = 0, j = 0;
    int ofs = 0, w = 0;
    int zeros = 0;

    while (j < n) {
        if (zeros <= m) {
            if (arr[j] == 0)
                zeros++;
            j++;
        }
        if (zeros > m) {
            if (arr[i] == 0)
                zeros--;
            i++;
        }
        if (j - i > w) {
            w = j - i;
            ofs = i;
        }
    }

    vector<int> best(w);
    iota(best.begin(), best.end(), ofs);

    return best;
}
```