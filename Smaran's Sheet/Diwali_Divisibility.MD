# 🪔 Diwali Divisibility

During the festival of **Diwali**, master artisans in Varanasi craft sacred oil lamps called **Divya Deepams**, each inscribed with a unique number. But not every lamp is worthy of lighting in the temple courtyard.

To receive the priest’s blessing, a lamp’s number `n` must obey the **Sacred Divisibility Rule**:

> The number `n` must be divisible by the **sum** of:
> - Its **digit sum** (the total of all its digits), and  
> - Its **digit product** (the result of multiplying all its digits together).

If the lamp obeys this rule, return `true` — it is blessed and may glow in the temple.

If not, return `false` — it must be returned to the artisan for remaking before the festival begins.

---

## Constraints

- `1 <= n <= 10⁶`

---

## Test Cases

#### Test Case 1
**Input:** `n = 99`  
**Output:** `true`  
**Explanation:**  
Digit sum = 9 + 9 = 18  
Digit product = 9 × 9 = 81  
Sum = 18 + 81 = 99  
99 is divisible by 99 → Lamp is blessed.

---

#### Test Case 2
**Input:** `n = 23`  
**Output:** `false`  
**Explanation:**  
Digit sum = 2 + 3 = 5  
Digit product = 2 × 3 = 6  
Sum = 5 + 6 = 11  
23 is not divisible by 11 → Lamp is not blessed.

---

#### Test Case 3
**Input:** `n = 90`  
**Output:** `true`  
**Explanation:**  
Digit sum = 9 + 0 = 9  
Digit product = 9 × 0 = 0  
Sum = 9 + 0 = 9  
90 is divisible by 9 → Lamp is blessed.

---

#### Test Case 4
**Input:** `n = 1`  
**Output:** `false`  
**Explanation:**  
Digit sum = 1  
Digit product = 1  
Sum = 1 + 1 = 2  
1 is not divisible by 2 → Lamp is not blessed.

---

#### Test Case 5
**Input:** `n = 22`  
**Output:** `false`  
**Explanation:**  
Digit sum = 2 + 2 = 4  
Digit product = 2 × 2 = 4  
Sum = 4 + 4 = 8  
22 is not divisible by 8 → Lamp is not blessed.

---

#### Test Case 6
**Input:** `n = 120`  
**Output:** `true`  
**Explanation:**  
Digit sum = 1 + 2 + 0 = 3  
Digit product = 1 × 2 × 0 = 0  
Sum = 3 + 0 = 3  
120 is divisible by 3 → Lamp is blessed.

---

#### Test Case 7
**Input:** `n = 505`  
**Output:** `false`  
**Explanation:**  
Digit sum = 5 + 0 + 5 = 10  
Digit product = 5 × 0 × 5 = 0  
Sum = 10 + 0 = 10  
505 is not divisible by 10 → Lamp is not blessed.

