[5. Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)
---

`String` `Dynamic Programming` `Palindrome`

use Manacher's algorithm can get O(n) solution, but it's diffcult

```java
public String longestPalindrome(String s) {
  if (s == null || s.length() == 0)
    return "";
  int start = 0, end = 0;
  for (int i = 0; i < s.length(); i++) {
    int len1 = getPalindromeLength(s, i, i);
    int len2 = getPalindromeLength(s, i, i + 1);
    int len = Math.max(len1, len2);
    if (len > end - start + 1) {
      start = i - (len - 1) / 2;
      end = i + len / 2;
    }
  }
  return s.substring(start, end + 1);
}

// Hint: return int
private int getPalindromeLength(String s, int left, int right) {
  int l = left;
  int r = right;
  int length = 0;
  while (l >= 0 && r < s.length() && s.charAt(l) == s.charAt(r)) {
    length = r - l + 1; // (r - 1) -  (l + 1) + 1 = r - l - 1
    l--;
    r++;
  }
  return length;
}
```
