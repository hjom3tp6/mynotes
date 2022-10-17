[3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
---

`String` `Sliding Window`

use HashMap

```java
public int lengthOfLongestSubstring(String s) {
  Map<Character, Integer> map = new HashMap<>();
  int start = 0, len = 0;
  for (int i = 0; i < s.length(); i++) {
    char c = s.charAt(i);
    if (map.containsKey(c) && map.get(c) >= start) { // ex. "abba" the len will be 3
      start = map.get(c) + 1;
    }
    len = Math.max(len, i - start + 1);
    map.put(c, i);
  }
  return len;
}
```

use array as map

```java
public int lengthOfLongestSubstring_array(String s) {
  if (s == null || s.length() < 1)
    return 0;
  Integer[] chars = new Integer[128];
  int left = 0, right = 0, maxLength = 0;
  int sLength = s.length();
  while (right < sLength) {
    char c = s.charAt(right); // declare key and value if use array, because it's very confused
    Integer idx = chars[c];
    if (idx != null && idx >= left) {
      left = chars[c] + 1;
    }
    maxLength = Math.max(maxLength, right - left + 1);
    chars[c] = right;
    right++;
  }
  return maxLength;
}
```
