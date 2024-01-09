---
title: 0443 String Compression
summary: 0443 String Compression LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
aliases: ["/posts/0443-string-compression", "/blog/posts/0443-string-compression", "/0443-string-compression"]
keywords: LeetCode, leetcode solution in Python3 C++ Java, 0443-string-compression solution
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_70_bold:0443 String Compression/problem-solving.webp
    alt: 0443 String Compression
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/string-compression/">443. String Compression</a></h2><h3>Medium</h3><hr><div><p>Given an array of characters <code>chars</code>, compress it using the following algorithm:</p>

<p>Begin with an empty string <code>s</code>. For each group of <strong>consecutive repeating characters</strong> in <code>chars</code>:</p>

<ul>
	<li>If the group's length is <code>1</code>, append the character to <code>s</code>.</li>
	<li>Otherwise, append the character followed by the group's length.</li>
</ul>

<p>The compressed string <code>s</code> <strong>should not be returned separately</strong>, but instead, be stored <strong>in the input character array <code>chars</code></strong>. Note that group lengths that are <code>10</code> or longer will be split into multiple characters in <code>chars</code>.</p>

<p>After you are done <strong>modifying the input array,</strong> return <em>the new length of the array</em>.</p>

<p>You must write an algorithm that uses only constant extra space.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> chars = ["a","a","b","b","c","c","c"]
<strong>Output:</strong> Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]
<strong>Explanation:</strong> The groups are "aa", "bb", and "ccc". This compresses to "a2b2c3".
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> chars = ["a"]
<strong>Output:</strong> Return 1, and the first character of the input array should be: ["a"]
<strong>Explanation:</strong> The only group is "a", which remains uncompressed since it's a single character.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre><strong>Input:</strong> chars = ["a","b","b","b","b","b","b","b","b","b","b","b","b"]
<strong>Output:</strong> Return 4, and the first 4 characters of the input array should be: ["a","b","1","2"].
<strong>Explanation:</strong> The groups are "a" and "bbbbbbbbbbbb". This compresses to "ab12".</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= chars.length &lt;= 2000</code></li>
	<li><code>chars[i]</code> is a lowercase English letter, uppercase English letter, digit, or symbol.</li>
</ul>
</div>

---




```python
class Solution:
    def compress(self, chars: List[str]) -> int:

        if len(chars)==1:
            return 1
        
        prev_char = chars[0]
        cnt = 1
        ptr = 0
        n = len(chars)

        # This function fills in the chars array with prev_char
        # and digits of cnt if necessary.
        def modify():
            nonlocal prev_char, ptr, cnt
            chars[ptr] = prev_char
            ptr+=1
            if cnt>1:
                cnt = str(cnt)
                for j in range(len(cnt)):
                    chars[ptr]=cnt[j]
                    ptr+=1
            cnt = 1
            prev_char = curr_char

        for i in range(1,n):
            curr_char = chars[i]
            if curr_char==prev_char:
                cnt+=1
            else:
                modify()
        
        modify()
        return ptr            

```