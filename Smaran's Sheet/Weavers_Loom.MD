# Weaver’s Loom

In the ancient textile town of Kanchipuram, master weavers chant coded mantras while crafting sacred silk patterns. Each mantra — a string of letters and symbols — guides the loom to weave, unravel, mirror, or invert the growing pattern.

You are given a string `s` composed of lowercase English letters and three sacred symbols: `*`, `#`, and `%`.

Simulate the loom’s behavior as it processes the mantra from left to right:

- If the character is a lowercase letter, append it to the current pattern.
- If the character is `*`, remove the last character from the current pattern, if it exists.
- If the character is `#`, duplicate the entire current pattern and append it to itself.
- If the character is `%`, reverse the current pattern.

Return the final woven pattern after processing all characters in `s`.

---

## Constraints

- `1 <= s.length <= 20`
- `s` consists only of lowercase English letters and the characters `*`, `#`, `%`.

---

## Test Cases

### Test Case 1
**Input:** `s = "a#b%*"`  
**Output:** `"ba"`  
**Explanation:**  
Step 0: 'a' → "a"  
Step 1: '#' → "aa"  
Step 2: 'b' → "aab"  
Step 3: '%' → "baa"  
Step 4: '*' → "ba"

---

### Test Case 2
**Input:** `s = "z*#"`  
**Output:** `""`  
**Explanation:**  
Step 0: 'z' → "z"  
Step 1: '*' → ""  
Step 2: '#' → ""

---

### Test Case 3
**Input:** `s = "ab*#"`  
**Output:** `"aa"`  
**Explanation:**  
Step 0: 'a' → "a"  
Step 1: 'b' → "ab"  
Step 2: '*' → "a"  
Step 3: '#' → "aa"

---

### Test Case 4
**Input:** `s = "a%b"`  
**Output:** `"ab"`  
**Explanation:**  
Step 0: 'a' → "a"  
Step 1: '%' → "a"  
Step 2: 'b' → "ab"

---

### Test Case 5
**Input:** `s = "a#%b"`  
**Output:** `"aab"`  
**Explanation:**  
Step 0: 'a' → "a"  
Step 1: '#' → "aa"  
Step 2: '%' → "aa"  
Step 3: 'b' → "aab"

---

### Test Case 6
**Input:** `s = "ab#c*"`  
**Output:** `"abab"`  
**Explanation:**  
Step 0: 'a' → "a"  
Step 1: 'b' → "ab"  
Step 2: '#' → "abab"  
Step 3: 'c' → "ababc"  
Step 4: '*' → "abab"

---

### Test Case 7
**Input:** `s = "a%#"`  
**Output:** `"aa"`  
**Explanation:**  
Step 0: 'a' → "a"  
Step 1: '%' → "a"  
Step 2: '#' → "aa"
