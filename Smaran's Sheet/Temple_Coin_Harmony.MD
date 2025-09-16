# Temple Coin Harmony

In a South Indian temple, two devotees climb the sacred steps to make offerings:

- **Devotee A** places one coin on each of the first `n` **odd-numbered** steps: Step 1, 3, 5, ..., up to the nth odd step.
- **Devotee B** places one coin on each of the first `n` **even-numbered** steps: Step 2, 4, 6, ..., up to the nth even step.

At the end of the ritual, the temple treasurer collects all coins from both devotees and wants to redistribute them equally among temple funds — splitting them into **identical portions with no remainder**.

Your task is to find the **largest possible portion size** — that is, the **GCD** (Greatest Common Divisor) of the total coins from Devotee A and Devotee B.

---

## Constraints:

- `1 <= n <= 1000`

---

## Test Cases:

#### Test Case 1
**Input:** `n = 4`  
**Output:** `4`  
**Explanation:**  
- Devotee A: Steps 1, 3, 5, 7 → 4 coins → total = 1 + 3 + 5 + 7 = **16**  
- Devotee B: Steps 2, 4, 6, 8 → 4 coins → total = 2 + 4 + 6 + 8 = **20**  
- GCD(16, 20) = **4** → Each fund gets 4 coins.

---

#### Test Case 2
**Input:** `n = 5`  
**Output:** `5`  
**Explanation:**  
- Devotee A: 1 + 3 + 5 + 7 + 9 = **25**  
- Devotee B: 2 + 4 + 6 + 8 + 10 = **30**  
- GCD(25, 30) = **5**

---

#### Test Case 3
**Input:** `n = 1`  
**Output:** `1`  
**Explanation:**  
- Devotee A: Step 1 → total = **1**  
- Devotee B: Step 2 → total = **2**  
- GCD(1, 2) = **1**

---

#### Test Case 4
**Input:** `n = 3`  
**Output:** `3`  
**Explanation:**  
- Devotee A: 1 + 3 + 5 = **9**  
- Devotee B: 2 + 4 + 6 = **12**  
- GCD(9, 12) = **3**

---

#### Test Case 5
**Input:** `n = 6`  
**Output:** `6`  
**Explanation:**  
- Devotee A: 1 + 3 + 5 + 7 + 9 + 11 = **36**  
- Devotee B: 2 + 4 + 6 + 8 + 10 + 12 = **42**  
- GCD(36, 42) = **6**

---

#### Test Case 6
**Input:** `n = 7`  
**Output:** `7`  
**Explanation:**  
- Devotee A: 1 + 3 + 5 + 7 + 9 + 11 + 13 = **49**  
- Devotee B: 2 + 4 + 6 + 8 + 10 + 12 + 14 = **56**  
- GCD(49, 56) = **7**

---

#### Test Case 7
**Input:** `n = 10`  
**Output:** `10`  
**Explanation:**  
- Devotee A: Sum of first 10 odd numbers = 10² = **100**  
- Devotee B: Sum of first 10 even numbers = 10×11 = **110**  
- GCD(100, 110) = **10**
