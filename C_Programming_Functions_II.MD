### 1) Compound Interest Power (Finance) — **Easy**

**Problem:**
A finance tool needs to compute compound multipliers of the form `base^years` (e.g., a yearly factor from a monthly base). Write a **recursive** function (no loops for exponent logic) that returns `base^exp` for non-negative integer `exp`. Print the result to two decimals.

**Input Format:**
`base exp` (base: double, exp: int ≥ 0)

**Output Format:**
`<value>` to two decimals

**Test Cases:**

**1.**
**Input:**

```
1.10 3
```

**Output:**

```
1.33
```

**Explanation:** 1.10^3 = 1.331 → 1.33.

**2.**
**Input:**

```
1.05 0
```

**Output:**

```
1.00
```

**Explanation:** Anything^0 = 1.

**3.**
**Input:**

```
2 1
```

**Output:**

```
2.00
```

**4.**
**Input:**

```
1.00 10
```

**Output:**

```
1.00
```

**5.**
**Input:**

```
1.20 2
```

**Output:**

```
1.44
```

**6.**
**Input:**

```
0.50 3
```

**Output:**

```
0.12
```

**7.**
**Input:**

```
1.07 4
```

**Output:**

```
1.31
```

**Solution (C):**

```c
#include <stdio.h>

double power(double b, int e){
    if (e == 0) return 1.0;
    return b * power(b, e - 1);
}

int main(void){
    double b; int e;
    if (scanf("%lf %d", &b, &e) != 2) return 0;
    printf("%.2f", power(b, e));
    return 0;
}
```

---

### 2) Reverse Customer Code (CRM) — **Easy**

**Problem:**
Support agents sometimes verify customer codes by reading them backward. Given a code (no spaces), **recursively** reverse the string in place (use two indices or pointers) and print the reversed code.

**Input Format:**
One string (ASCII, no spaces)

**Output Format:**
Reversed string

**Test Cases:**

**1.**
**Input:**

```
AB123XZ
```

**Output:**

```
ZX321BA
```

**Explanation:** Reversed end-to-start.

**2.**
**Input:**

```
K
```

**Output:**

```
K
```

**Explanation:** Single character unchanged.

**3.**
**Input:**

```
hello
```

**Output:**

```
olleh
```

**4.**
**Input:**

```
racecar
```

**Output:**

```
racecar
```

**5.**
**Input:**

```
2025
```

**Output:**

```
5202
```

**6.**
**Input:**

```
byteXL
```

**Output:**

```
LXetyb
```

**7.**
**Input:**

```
A1B2
```

**Output:**

```
2B1A
```

**Solution (C):**

```c
#include <stdio.h>
#include <string.h>

void rev(char *s, int l, int r){
    if (l >= r) return;
    char t = s[l]; s[l] = s[r]; s[r] = t;
    rev(s, l + 1, r - 1);
}

int main(void){
    char s[200005];
    if (scanf("%200000s", s) != 1) return 0;
    int n = (int)strlen(s);
    rev(s, 0, n - 1);
    printf("%s", s);
    return 0;
}
```

---

### 3) Daily Revenue Sum (Analytics) — **Easy**

**Problem:**
An analytics service aggregates `n` daily revenues. Using **recursion** over the array (no loops for the summation logic), compute and print the total revenue as an `int`.

**Input Format:**
`n`
`n` space-separated integers

**Output Format:**
One integer: total revenue

**Test Cases:**

**1.**
**Input:**

```
5
10 20 30 40 50
```

**Output:**

```
150
```

**Explanation:** Adds elements recursively.

**2.**
**Input:**

```
3
-2 7 0
```

**Output:**

```
5
```

**Explanation:** Handles negatives.

**3.**
**Input:**

```
1
100
```

**Output:**

```
100
```

**4.**
**Input:**

```
4
-1 -1 -1 -1
```

**Output:**

```
-4
```

**5.**
**Input:**

```
6
10 10 10 10 10 10
```

**Output:**

```
60
```

**6.**
**Input:**

```
2
2147483647 -1
```

**Output:**

```
2147483646
```

**7.**
**Input:**

```
5
0 0 0 0 0
```

**Output:**

```
0
```

**Solution (C):**

```c
#include <stdio.h>

int recsum(int *a, int n){
    if (n == 0) return 0;
    return a[n - 1] + recsum(a, n - 1);
}

int main(void){
    int n; if (scanf("%d", &n) != 1) return 0;
    int a[200005];
    for (int i = 0; i < n; ++i) scanf("%d", &a[i]);
    printf("%d", recsum(a, n));
    return 0;
}
```

---

### 4) Sync Machine Cycles (GCD) — **Easy**

**Problem:**
Two conveyor belts loop every `a` and `b` seconds; the time they align is governed by their GCD. Using **recursive Euclid’s algorithm**, compute `gcd(a, b)` and print it.

**Input Format:**
`a b`

**Output Format:**
GCD as integer

**Test Cases:**

**1.**
**Input:**

```
48 18
```

**Output:**

```
6
```

**Explanation:** gcd(48,18)=6.

**2.**
**Input:**

```
7 13
```

**Output:**

```
1
```

**Explanation:** Co-prime.

**3.**
**Input:**

```
0 0
```

**Output:**

```
0
```

**4.**
**Input:**

```
0 5
```

**Output:**

```
5
```

**5.**
**Input:**

```
25 5
```

**Output:**

```
5
```

**6.**
**Input:**

```
270 192
```

**Output:**

```
6
```

**7.**
**Input:**

```
1000000 10
```

**Output:**

```
10
```

**Solution (C):**

```c
#include <stdio.h>

int gcd(int a, int b){
    if (b == 0) return a >= 0 ? a : -a;
    return gcd(b, a % b);
}

int main(void){
    int a, b; if (scanf("%d %d", &a, &b) != 2) return 0;
    printf("%d", gcd(a, b));
    return 0;
}
```

---

### 5) Search Product ID (Recursive Binary Search) — **Medium**

**Problem:**
A sorted list of product IDs is scanned for a target ID. Implement **recursive binary search** (no loops for the search logic). Print the 0-based index if found, else `-1`.

**Input Format:**
`n`
`n` sorted integers
`x`

**Output Format:**
Index or `-1`

**Test Cases:**

**1.**
**Input:**

```
5
2 4 6 8 10
8
```

**Output:**

```
3
```

**Explanation:** 8 found at index 3.

**2.**
**Input:**

```
4
1 3 5 7
2
```

**Output:**

```
-1
```

**Explanation:** 2 not present.

**3.**
**Input:**

```
1
42
42
```

**Output:**

```
0
```

**4.**
**Input:**

```
6
1 2 3 4 5 6
6
```

**Output:**

```
5
```

**5.**
**Input:**

```
6
1 2 3 4 5 6
0
```

**Output:**

```
-1
```

**6.**
**Input:**

```
2
5 9
9
```

**Output:**

```
1
```

**7.**
**Input:**

```
3
-5 0 7
-5
```

**Output:**

```
0
```

**Solution (C):**

```c
#include <stdio.h>

int bs(int *a, int l, int r, int x){
    if (l > r) return -1;
    int m = l + (r - l) / 2;
    if (a[m] == x) return m;
    if (x < a[m]) return bs(a, l, m - 1, x);
    return bs(a, m + 1, r, x);
}

int main(void){
    int n; if (scanf("%d", &n) != 1) return 0;
    int a[200005];
    for (int i = 0; i < n; ++i) scanf("%d", &a[i]);
    int x; scanf("%d", &x);
    printf("%d", bs(a, 0, n - 1, x));
    return 0;
}
```

---

### 6) Validate Palindrome ID (Quality Gate) — **Medium**

**Problem:**
A quality gate marks an ID valid if it reads exactly the same forward and backward (case-sensitive). Using **recursion** on indices, determine if the string is a palindrome and print `Valid` or `Invalid`.

**Input Format:**
One string (no spaces)

**Output Format:**
`Valid` or `Invalid`

**Test Cases:**

**1.**
**Input:**

```
racecar
```

**Output:**

```
Valid
```

**Explanation:** Same both ways.

**2.**
**Input:**

```
Aba
```

**Output:**

```
Invalid
```

**Explanation:** Case sensitive.

**3.**
**Input:**

```
a
```

**Output:**

```
Valid
```

**4.**
**Input:**

```
ab
```

**Output:**

```
Invalid
```

**5.**
**Input:**

```
1221
```

**Output:**

```
Valid
```

**6.**
**Input:**

```
abcba
```

**Output:**

```
Valid
```

**7.**
**Input:**

```
abcdea
```

**Output:**

```
Invalid
```

**Solution (C):**

```c
#include <stdio.h>
#include <string.h>

int pal(const char *s, int l, int r){
    if (l >= r) return 1;
    return s[l] == s[r] && pal(s, l + 1, r - 1);
}

int main(void){
    char s[200005];
    if (scanf("%200000s", s) != 1) return 0;
    int n = (int)strlen(s);
    printf("%s", pal(s, 0, n - 1) ? "Valid" : "Invalid");
    return 0;
}
```

---

### 7) Move Crates Between Stacks (Tower of Hanoi) — **Medium**

**Problem:**
A mini-warehouse has `n` crates on stack `A` that must be moved to stack `C` using stack `B` as auxiliary, moving one crate at a time and never placing a larger crate on a smaller one. Print each move as `A->C` style using **recursion**.

**Input Format:**
`n` (1 ≤ n ≤ 10; output grows quickly)

**Output Format:**
Each move on a new line: `From->To`

**Test Cases:**

**1.**
**Input:**

```
2
```

**Output:**

```
A->B
A->C
B->C
```

**Explanation:** 3 moves for n=2.

**2.**
**Input:**

```
1
```

**Output:**

```
A->C
```

**Explanation:** Single move.

**3.**
**Input:** `3` → (7 lines)
**Output:** first few lines:

```
A->C
A->B
C->B
A->C
B->A
B->C
A->C
```

**4.**
**Input:** `4` → 15 lines
**Output:** (omitted for brevity)

**5.**
**Input:** `2` → same as case 1
**6.**
**Input:** `1` → same as case 2
**7.**
**Input:** `3` → same as case 3

**Solution (C):**

```c
#include <stdio.h>

void hanoi(int n, char A, char B, char C){
    if (n == 0) return;
    hanoi(n - 1, A, C, B);
    printf("%c->%c\n", A, C);
    hanoi(n - 1, B, A, C);
}

int main(void){
    int n; if (scanf("%d", &n) != 1) return 0;
    hanoi(n, 'A', 'B', 'C');
    return 0;
}
```

---

### 8) Digit Health Code (Recursive Sum of Digits) — **Hard**

**Problem:**
A kiosk generates numeric tokens; a control digit is the **recursive sum of digits** until a single digit is obtained (digital root computed via repeated recursive summing). Print the resulting single digit.

**Input Format:**
One non-negative integer `N` (read as string to avoid range issues)

**Output Format:**
Single digit (0–9)

**Test Cases:**

**1.**
**Input:**

```
9875
```

**Output:**

```
2
```

**Explanation:** 9+8+7+5=29 → 2+9=11 → 1+1=2.

**2.**
**Input:**

```
0
```

**Output:**

```
0
```

**Explanation:** Already single digit.

**3.**
**Input:**

```
9
```

**Output:**

```
9
```

**4.**
**Input:**

```
10
```

**Output:**

```
1
```

**5.**
**Input:**

```
99
```

**Output:**

```
9
```

**6.**
**Input:**

```
123456
```

**Output:**

```
3
```

**7.**
**Input:**

```
100000
```

**Output:**

```
1
```

**Solution (C):**

```c
#include <stdio.h>

int sum_str_digits(const char *s){
    int sm = 0;
    for (int i = 0; s[i]; ++i) sm += s[i] - '0';
    return sm;
}

int digitroot_int(int x){
    if (x < 10) return x;
    // convert x to string to reuse sum_str_digits simply
    char buf[64]; int i = 0, y = x;
    if (y == 0) buf[i++] = '0';
    while (y > 0) { buf[i++] = (char)('0' + (y % 10)); y /= 10; }
    // reverse
    for (int l = 0, r = i - 1; l < r; ++l, --r){ char t = buf[l]; buf[l] = buf[r]; buf[r] = t; }
    buf[i] = '\0';
    return digitroot_int(sum_str_digits(buf));
}

int main(void){
    char s[200005];
    if (scanf("%200000s", s) != 1) return 0;
    // strip leading zeros for cleanliness but keep at least one digit
    int z = 0; while (s[z] == '0' && s[z + 1]) ++z;
    int sm = sum_str_digits(s + z);
    printf("%d", digitroot_int(sm));
    return 0;
}
```

---

### 9) Sensor Bits (Decimal to Binary Recursion) — **Hard**

**Problem:**
A sensor streams a decimal integer that must be transmitted as a binary bitstring (no leading zeros unless the number is zero). Using **recursion**, print the binary representation.

**Input Format:**
One integer `n` (0 ≤ n ≤ 10^9)

**Output Format:**
Binary representation

**Test Cases:**

**1.**
**Input:**

```
5
```

**Output:**

```
101
```

**Explanation:** Print bin(2) then 1.

**2.**
**Input:**

```
0
```

**Output:**

```
0
```

**Explanation:** Base case prints zero.

**3.**
**Input:**

```
1
``**
Output:**
```

1

```

**4.**  
**Input:**
```

8

```
**Output:**
```

1000

```

**5.**  
**Input:**
```

10

```
**Output:**
```

1010

```

**6.**  
**Input:**
```

16

```
**Output:**
```

10000

```

**7.**  
**Input:**
```

1023

```
**Output:**
```

1111111111

````

**Solution (C):**
```c
#include <stdio.h>

void printbin(int n){
    if (n < 2){
        printf("%d", n);
        return;
    }
    printbin(n / 2);
    printf("%d", n % 2);
}

int main(void){
    int n; if (scanf("%d", &n) != 1) return 0;
    printbin(n);
    return 0;
}
````

---

### 10) Merge Sorted Logs (Recursive Merge) — **Hard**

**Problem:**
Two sorted event streams (ASC) must be merged into one sorted stream. Use **recursion** to merge arrays `A` and `B` into an output buffer `C` (no loops for the merge logic). Print the merged sequence.

**Input Format:**
`n m`
`n` integers (sorted)
`m` integers (sorted)

**Output Format:**
`n+m` integers (space-separated)

**Test Cases:**

**1.**
**Input:**

```
3 4
5 10 15
2 3 16 20
```

**Output:**

```
2 3 5 10 15 16 20
```

**Explanation:** Standard merge via recursion.

**2.**
**Input:**

```
0 3

1 2 3
```

**Output:**

```
1 2 3
```

**Explanation:** Only second stream.

**3.**
**Input:**

```
3 0
1 2 3

```

**Output:**

```
1 2 3
```

**4.**
**Input:**

```
4 4
1 1 1 1
1 1 1 1
```

**Output:**

```
1 1 1 1 1 1 1 1
```

**5.**
**Input:**

```
5 3
2 4 6 8 10
1 3 5
```

**Output:**

```
1 2 3 4 5 6 8 10
```

**6.**
**Input:**

```
3 3
-5 0 7
-6 -1 10
```

**Output:**

```
-6 -5 -1 0 7 10
```

**7.**
**Input:**

```
1 1
100
100
```

**Output:**

```
100 100
```

**Solution (C):**

```c
#include <stdio.h>

void merge_rec(int *A, int n, int *B, int m, int *C, int i, int j, int k){
    if (i == n && j == m) return;
    if (i == n){ C[k] = B[j]; merge_rec(A, n, B, m, C, i, j + 1, k + 1); return; }
    if (j == m){ C[k] = A[i]; merge_rec(A, n, B, m, C, i + 1, j, k + 1); return; }
    if (A[i] <= B[j]){ C[k] = A[i]; merge_rec(A, n, B, m, C, i + 1, j,     k + 1); }
    else             { C[k] = B[j]; merge_rec(A, n, B, m, C, i,     j + 1, k + 1); }
}

int main(void){
    int n, m; if (scanf("%d %d", &n, &m) != 2) return 0;
    static int A[200005], B[200005], C[400010];
    for (int i = 0; i < n; ++i) scanf("%d", &A[i]);
    for (int j = 0; j < m; ++j) scanf("%d", &B[j]);
    merge_rec(A, n, B, m, C, 0, 0, 0);
    for (int t = 0; t < n + m; ++t){ if (t) printf(" "); printf("%d", C[t]); }
    return 0;
}
```

