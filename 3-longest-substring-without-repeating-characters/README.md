## Add Two Numbers
**Difficulty:** Medium<br>

[LEETCODE_LINK](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

One of the solutions that I am proud of!

**Question:**

Given a string s, find the length of the longest substring without repeating characters.

**Example:**

```
Example 1:
| Input: s = "abcabcbb"
| Output: 3
| Explanation: The answer is "abc", with the length of 3.

Example 2:
| Input: s = "bbbbb"
| Output: 1
| Explanation: The answer is "b", with the length of 1.

Example 3:
| Input: s = "pwwkew"
| Output: 3
| Explanation: The answer is "wke", with the length of 3.
| Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

**Solution:** Golang

``` go
func lengthOfLongestSubstring(s string) int {
	max_seen := 0
	seen_arr := [260]int{}
	l := 0
    var val byte = 0
	for x := 0; x < len(s); x++ {
        val = s[x]-97
		for seen_arr[val] != 0 && seen_arr[val] >= l {
			if seen_arr[val] <= l+1 {
				seen_arr[val] = 0
			}
			l++
		}
		if max_seen < x-l+1 {
			max_seen = x - l + 1
		}
		seen_arr[val] = x + 1
	}

	return max_seen
}
```

**Performance:**
Runtime 0ms (Beats 100% users) <br>

![Performance](./performance.png)

Memory 2ms (Beats 98.06% users) <br>

![Memory](./memory.png)