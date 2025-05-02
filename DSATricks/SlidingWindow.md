# Sliding Window Pattern

Sliding Window is a common technique used for 
- solving substring, 
- subarray, and 
- sequence problems efficiently. 

There are two main variations:

---

## 1. Longest Substring Without Repeating Characters (All Unique)

### ✨ Key Concepts
- Use a **Set** or **Map** to track characters in the current window
- Expand the window with `right`, shrink from `left` until window has all unique characters
- Update max length whenever window is valid

### 📁 Java Code Using Set
```java
public int lengthOfLongestSubstring(String s) {
    Set<Character> uniqueChars = new HashSet<>();
    int left = 0, maxLength = 0;

    for (int right = 0; right < s.length(); right++) {
        char rightChar = s.charAt(right);
        while (uniqueChars.contains(rightChar)) {
            uniqueChars.remove(s.charAt(left));
            left++;
        }
        uniqueChars.add(rightChar);
        maxLength = Math.max(maxLength, right - left + 1);
    }

    return maxLength;
}
```
### 💡 Tips to Remember
- Use while (not if) to remove all duplicates 
- Update maxLength after inserting the new character 
- Pattern: expand with right, clean up with left

## 2. Longest Substring with At Most K Distinct Characters

This variation of the sliding window pattern is useful when you need to find the **longest substring** with **at most K distinct characters**.

### ✨ Key Concepts

- Use a **HashMap<Character, Integer>** to count character frequencies in the current window.
- Expand the window using a `right` pointer.
- Shrink the window using a `left` pointer **while the number of distinct characters exceeds `k`**.
- Update `maxLength` each time the window is valid.

---

## 📁 Java Implementation

```java
public int lengthOfLongestSubstringKDistinct(String s, int k) {
    if (s == null || s.length() == 0 || k == 0) return 0;

    Map<Character, Integer> freqMap = new HashMap<>();
    int left = 0, maxLength = 0;

    for (int right = 0; right < s.length(); right++) {
        char rightChar = s.charAt(right);
        freqMap.put(rightChar, freqMap.getOrDefault(rightChar, 0) + 1);

        while (freqMap.size() > k) {
            char leftChar = s.charAt(left);
            freqMap.put(leftChar, freqMap.get(leftChar) - 1);
            if (freqMap.get(leftChar) == 0) {
                freqMap.remove(leftChar);
            }
            left++;
        }

        maxLength = Math.max(maxLength, right - left + 1);
    }

    return maxLength;
}
```
### 💡 Tips to Remember
- Always use while (map.size() > k) to ensure you shrink fully until the window is valid.
- Think of the map as your window state.
- Update maxLength after window is valid. 
- Works for variations like:
  - Longest substring with at most 2 distinct characters 
  - Longest substring with at most K vowels or consonants 
  - Sliding window over arrays (with keys being numbers instead of chars)

## 🔁 Base Template
```java
Map<Character, Integer> map = new HashMap<>();
int left = 0;

for (int right = 0; right < s.length(); right++) {
    // Add s.charAt(right) to map
    while (map.size() > k) {
        // Shrink from left
        map.remove/s.decrease left count
        left++;
    }
    // Update maxLength
}
```
## Summary

## 🔁 Sliding Window Pattern Summary

| Pattern Type                  | What to Track             | Shrink Condition            | Common Problem                                     |
|------------------------------|---------------------------|-----------------------------|----------------------------------------------------|
| Unique characters            | Set / Map                 | `while duplicate exists`    | Longest substring without repeating characters     |
| At most K distinct characters| Map (count frequency)     | `while map.size() > k`      | Longest substring with at most K distinct chars    |


