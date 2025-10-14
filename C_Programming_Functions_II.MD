### 1) Final Bill After Discount (Retail Checkout) — **Easy**

**Problem:**
At a retail counter, each bill has a gross amount and a discount percentage. Write a program that defines a function to compute the final bill as `gross - (gross * discount / 100)` using **call by value** and prints the final amount to two decimals.

**Input Format:**
Two numbers: `gross discount_percent`

**Output Format:**
Final amount to two decimals

**Test Cases:**

**1.**
**Input:**

```
1000 10
```

**Output:**

```
900.00
```

**Explanation:** 10% of 1000 is 100; 1000 − 100 = 900.

**2.**
**Input:**

```
799.99 12.5
```

**Output:**

```
699.99
```

**Explanation:** Discount = 99.99875 → final 699.99125 → prints 699.99.

**3.**
**Input:**

```
0 50
```

**Output:**

```
0.00
```

**4.**
**Input:**

```
250 0
```

**Output:**

```
250.00
```

**5.**
**Input:**

```
500 100
``**
Output:**
```

0.00

```

**6.**  
**Input:**
```

1234.56 1.2

```
**Output:**
```

1219.74

```

**7.**  
**Input:**
```

999.95 5

```
**Output:**
```

949.95

````

**Solution (C):**
```c
#include <stdio.h>

double final_amount(double gross, double disc) { // declaration + definition
    return gross - (gross * disc / 100.0);       // call-by-value
}

int main(void) {
    double g, d;
    if (scanf("%lf %lf", &g, &d) != 2) return 0;
    printf("%.2f", final_amount(g, d));          // invocation
    return 0;
}
````

---

### 2) Swap Seat Counts (Event Hall) — **Easy**

**Problem:**
Two sections of an event hall have interchanged seat counts in software due to a data entry mistake. Define a function that **swaps two integers via pointers (call by reference)** and print the corrected order.

**Input Format:**
Two integers: `A B`

**Output Format:**
`A B` after swap

**Test Cases:**

**1.**
**Input:**

```
120 300
```

**Output:**

```
300 120
```

**Explanation:** Values interchanged using pointer parameters.

**2.**
**Input:**

```
0 0
```

**Output:**

```
0 0
```

**Explanation:** Swapping equal zeroes stays zero.

**3.**
**Input:**

```
5 5
```

**Output:**

```
5 5
```

**4.**
**Input:**

```
-10 50
```

**Output:**

```
50 -10
```

**5.**
**Input:**

```
1 2
```

**Output:**

```
2 1
```

**6.**
**Input:**

```
999 -999
```

**Output:**

```
-999 999
```

**7.**
**Input:**

```
42 0
```

**Output:**

```
0 42
```

**Solution (C):**

```c
#include <stdio.h>

void swap_int(int *a, int *b) { int t = *a; *a = *b; *b = t; }

int main(void) {
    int a, b; if (scanf("%d %d", &a, &b) != 2) return 0;
    swap_int(&a, &b);
    printf("%d %d", a, b);
    return 0;
}
```

---

### 3) Apply Service Charge (Restaurant Bills) — **Easy**

**Problem:**
A restaurant system applies a uniform service charge percentage to every bill in a day. Define a function that takes an array of bill totals and updates each value **in place** using pointers (no recursion). Print the updated totals rounded to two decimals on one line separated by spaces.

**Input Format:**
`n`
`n` bill amounts (floats)
`charge_percent`

**Output Format:**
`n` updated amounts to two decimals (space-separated)

**Test Cases:**

**1.**
**Input:**

```
3
100 200 300
10
```

**Output:**

```
110.00 220.00 330.00
```

**Explanation:** +10% to each bill.

**2.**
**Input:**

```
4
50 75 25 100
0
```

**Output:**

```
50.00 75.00 25.00 100.00
```

**Explanation:** 0% keeps values same.

**3.**
**Input:**

```
1
99.99
5
```

**Output:**

```
104.99
```

**4.**
**Input:**

```
2
0 0
12
```

**Output:**

```
0.00 0.00
```

**5.**
**Input:**

```
5
10 20 30 40 50
-10
```

**Output:**

```
9.00 18.00 27.00 36.00 45.00
```

**6.**
**Input:**

```
3
1.11 2.22 3.33
50
```

**Output:**

```
1.67 3.33 5.00
```

**7.**
**Input:**

```
2
1000 0.01
1
```

**Output:**

```
1010.00 0.01
```

**Solution (C):**

```c
#include <stdio.h>

void apply_charge(double *arr, int n, double pct) {
    for (int i = 0; i < n; ++i) arr[i] += arr[i] * pct / 100.0;
}

int main(void) {
    int n; if (scanf("%d", &n) != 1) return 0;
    double a[200005];
    for (int i = 0; i < n; ++i) scanf("%lf", &a[i]);
    double p; scanf("%lf", &p);
    apply_charge(a, n, p);
    for (int i = 0; i < n; ++i) { if (i) printf(" "); printf("%.2f", a[i]); }
    return 0;
}
```

---

### 4) Safe Divide Orders (Warehouse Binning) — **Easy**

**Problem:**
A warehouse splits `total_items` evenly into boxes; any leftover is kept aside. Define a function that performs integer division safely without recursion: it should write the quotient and remainder to **output parameters** (pointers). Print `quotient remainder`.

**Input Format:**
`total_items boxes`

**Output Format:**
`quotient remainder`

**Test Cases:**

**1.**
**Input:**

```
100 6
```

**Output:**

```
16 4
```

**Explanation:** 100/6 = 16 remainder 4.

**2.**
**Input:**

```
9 3
```

**Output:**

```
3 0
```

**Explanation:** Exactly divisible.

**3.**
**Input:**

```
7 10
```

**Output:**

```
0 7
```

**4.**
**Input:**

```
0 5
```

**Output:**

```
0 0
```

**5.**
**Input:**

```
25 4
```

**Output:**

```
6 1
```

**6.**
**Input:**

```
-7 3
```

**Output:**

```
-2 -1
```

**7.**
**Input:**

```
7 -3
```

**Output:**

```
-2 1
```

**Solution (C):**

```c
#include <stdio.h>

void safe_divide(int a, int b, int *q, int *r) {
    if (b == 0) { *q = 0; *r = 0; return; }
    *q = a / b;
    *r = a % b; // C remainder keeps sign of dividend
}

int main(void) {
    int total, boxes; if (scanf("%d %d", &total, &boxes) != 2) return 0;
    int q, r; safe_divide(total, boxes, &q, &r);
    printf("%d %d", q, r);
    return 0;
}
```

---

### 5) Running Ticket IDs (Support Desk) — **Medium**

**Problem:**
A helpdesk assigns a new ticket ID each time a request is processed during the program run. Define a function `next_id()` with a **static local variable** that increases on every call, starting at 1. Given `n`, print the sequence of `n` ticket IDs separated by spaces.

**Input Format:**
`n`

**Output Format:**
`n` IDs (1-based, space-separated)

**Test Cases:**

**1.**
**Input:**

```
5
```

**Output:**

```
1 2 3 4 5
```

**Explanation:** Static variable persists across calls.

**2.**
**Input:**

```
1
```

**Output:**

```
1
```

**Explanation:** Only one ID requested.

**3.**
**Input:**

```
3
```

**Output:**

```
1 2 3
```

**4.**
**Input:**

```
0
```

**Output:**

```
```

**5.**
**Input:**

```
2
```

**Output:**

```
1 2
```

**6.**
**Input:**

```
7
```

**Output:**

```
1 2 3 4 5 6 7
```

**7.**
**Input:**

```
10
```

**Output:**

```
1 2 3 4 5 6 7 8 9 10
```

**Solution (C):**

```c
#include <stdio.h>

int next_id(void) { static int id = 0; id += 1; return id; } // scope demo

int main(void) {
    int n; if (scanf("%d", &n) != 1) return 0;
    for (int i = 0; i < n; ++i) { if (i) printf(" "); printf("%d", next_id()); }
    return 0;
}
```

---

### 6) Mask Email Username (Privacy Tool) — **Medium**

**Problem:**
For privacy display, show an email by keeping its first and last username characters and replacing the middle of the username (before `@`) with asterisks. Define a function that **modifies the string in place** using pointers and **library `<ctype.h>`** to normalize to lowercase for the username only. Print the masked email (domain unchanged).

**Input Format:**
One email string (no spaces)

**Output Format:**
Masked email

**Test Cases:**

**1.**
**Input:**

```
Alice.Wonder@Example.com
```

**Output:**

```
a**********r@Example.com
```

**Explanation:** Username `Alice.Wonder` → lowercased; keep first `a` and last `r`, mask middle.

**2.**
**Input:**

```
X@site.io
```

**Output:**

```
x@site.io
```

**Explanation:** Single-char username stays as is (no middle to mask).

**3.**
**Input:**

```
ab@d.com
```

**Output:**

```
ab@d.com
```

**4.**
**Input:**

```
abc@d.com
```

**Output:**

```
a*c@d.com
```

**5.**
**Input:**

```
john_doe@company.org
```

**Output:**

```
j*******e@company.org
```

**6.**
**Input:**

```
USER@DOMAIN.COM
```

**Output:**

```
u**r@DOMAIN.COM
```

**7.**
**Input:**

```
manydots...here@host.net
```

**Output:**

```
m**************e@host.net
```

**Solution (C):**

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void mask(char *s) {
    char *at = strchr(s, '@');
    if (!at) return;
    // lowercase username
    for (char *p = s; p < at; ++p) *p = (char)tolower((unsigned char)*p);
    int len = (int)(at - s);
    if (len <= 1) return;              // nothing to mask
    if (len == 2) return;              // keep both
    // mask middle
    for (int i = 1; i < len - 1; ++i) s[i] = '*';
}

int main(void) {
    char email[200005];
    if (scanf("%200000s", email) != 1) return 0;
    mask(email);
    printf("%s", email);
    return 0;
}
```

---

### 7) Product Key Validator (Manufacturing) — **Medium**

**Problem:**
A production line prints product keys like `AB12-CD34`. Define a function that checks if a key is valid: exactly 9 chars with a hyphen at position 5, all others alphanumeric (use **library `<ctype.h>`**). Print `Valid` or `Invalid`.

**Input Format:**
One product key (no spaces)

**Output Format:**
`Valid` or `Invalid`

**Test Cases:**

**1.**
**Input:**

```
AB12-CD34
```

**Output:**

```
Valid
```

**Explanation:** Matches pattern.

**2.**
**Input:**

```
a1b2c-d3e4
```

**Output:**

```
Valid
```

**Explanation:** Case and digits allowed; hyphen at position 5.

**3.**
**Input:**

```
AB12CD34
```

**Output:**

```
Invalid
```

**4.**
**Input:**

```
AB12-CD3@
```

**Output:**

```
Invalid
```

**5.**
**Input:**

```
----CD34
```

**Output:**

```
Invalid
```

**6.**
**Input:**

```
1234-5678
```

**Output:**

```
Valid
```

**7.**
**Input:**

```
A23--567
```

**Output:**

```
Invalid
```

**Solution (C):**

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int valid_key(const char *s) {
    if ((int)strlen(s) != 9) return 0;
    for (int i = 0; i < 9; ++i) {
        if (i == 4) { if (s[i] != '-') return 0; }
        else if (!isalnum((unsigned char)s[i])) return 0;
    }
    return 1;
}

int main(void) {
    char key[64];
    if (scanf("%63s", key) != 1) return 0;
    printf("%s", valid_key(key) ? "Valid" : "Invalid");
    return 0;
}
```

---

### 8) KPI Summary (Min/Max/Average) — **Hard**

**Problem:**
An operations dashboard needs a quick KPI summary from `n` daily metrics. Define **three user-defined functions**: `min_val`, `max_val`, and `avg_val` (all non-recursive). Read `n` integers, then print `min max avg` where avg is to two decimals.

**Input Format:**
`n`
`n` space-separated integers

**Output Format:**
`min max avg` (avg to two decimals)

**Test Cases:**

**1.**
**Input:**

```
5
10 20 30 40 50
```

**Output:**

```
10 50 30.00
```

**Explanation:** Min=10, Max=50, Avg=30.00.

**2.**
**Input:**

```
4
-1 -1 -1 -1
```

**Output:**

```
-1 -1 -1.00
```

**Explanation:** All equal negatives.

**3.**
**Input:**

```
1
7
```

**Output:**

```
7 7 7.00
```

**4.**
**Input:**

```
3
0 0 1
```

**Output:**

```
0 1 0.33
```

**5.**
**Input:**

```
6
5 4 3 2 1 0
```

**Output:**

```
0 5 2.50
```

**6.**
**Input:**

```
3
100 100 101
```

**Output:**

```
100 101 100.33
```

**7.**
**Input:**

```
5
-5 0 5 -10 10
```

**Output:**

```
-10 10 0.00
```

**Solution (C):**

```c
#include <stdio.h>

int min_val(const int *a, int n) { int m = a[0]; for (int i=1;i<n;++i) if (a[i]<m) m=a[i]; return m; }
int max_val(const int *a, int n) { int m = a[0]; for (int i=1;i<n;++i) if (a[i]>m) m=a[i]; return m; }
double avg_val(const int *a, int n){ long long s=0; for(int i=0;i<n;++i) s+=a[i]; return (double)s/n; }

int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    int a[200005]; for (int i=0;i<n;++i) scanf("%d",&a[i]);
    printf("%d %d %.2f", min_val(a,n), max_val(a,n), avg_val(a,n));
    return 0;
}
```

---

### 9) Case-Insensitive Compare (Usernames) — **Hard**

**Problem:**
During login, two usernames should be considered equal ignoring letter case. Write a **user-defined function** that compares two strings case-insensitively using `<ctype.h>` (convert both to lower or upper while comparing) and returns -1, 0, or 1. Print the result.

**Input Format:**
Two strings `u v` (no spaces)

**Output Format:**
`-1` if `u < v`, `0` if equal, `1` if `u > v` (case-insensitive)

**Test Cases:**

**1.**
**Input:**

```
Alice alice
```

**Output:**

```
0
```

**Explanation:** Same ignoring case.

**2.**
**Input:**

```
beta Alpha
```

**Output:**

```
1
```

**Explanation:** `"beta"` > `"alpha"` lexicographically ignoring case.

**3.**
**Input:**

```
aa aB
```

**Output:**

```
-1
```

**4.**
**Input:**

```
Z zzz
```

**Output:**

```
-1
```

**5.**
**Input:**

```
dev DEV
```

**Output:**

```
0
```

**6.**
**Input:**

```
longName short
```

**Output:**

```
1
```

**7.**
**Input:**

```
abc abd
```

**Output:**

```
-1
```

**Solution (C):**

```c
#include <stdio.h>
#include <ctype.h>

int ci_cmp(const char *a, const char *b) {
    while (*a && *b) {
        int ca = tolower((unsigned char)*a);
        int cb = tolower((unsigned char)*b);
        if (ca < cb) return -1;
        if (ca > cb) return 1;
        ++a; ++b;
        }
    if (*a) return 1;
    if (*b) return -1;
    return 0;
}

int main(void) {
    char u[200005], v[200005];
    if (scanf("%200000s %200000s", u, v) != 2) return 0;
    printf("%d", ci_cmp(u, v));
    return 0;
}
```

---

### 10) Temperature Conversion Menu (IoT Gateway) — **Hard**

**Problem:**
An IoT gateway receives a reading and a unit code. Create two **user-defined functions**: `c_to_f` and `f_to_c`. If unit is `C`, convert Celsius to Fahrenheit; if `F`, convert Fahrenheit to Celsius. Show **function declaration, definition, and invocation** clearly, and print the converted value to two decimals.

**Input Format:**
`value unit` (unit is `C` or `F`)

**Output Format:**
Converted value to two decimals

**Test Cases:**

**1.**
**Input:**

```
0 C
```

**Output:**

```
32.00
```

**Explanation:** 0°C → 32°F.

**2.**
**Input:**

```
212 F
```

**Output:**

```
100.00
```

**Explanation:** 212°F → 100°C.

**3.**
**Input:**

```
25 C
```

**Output:**

```
77.00
```

**4.**
**Input:**

```
98.6 F
```

**Output:**

```
37.00
```

**5.**
**Input:**

```
-40 C
```

**Output:**

```
-40.00
```

**6.**
**Input:**

```
451 F
```

**Output:**

```
232.78
```

**7.**
**Input:**

```
15 C
```

**Output:**

```
59.00
```

**Solution (C):**

```c
#include <stdio.h>

// declarations
double c_to_f(double c);
double f_to_c(double f);

// definitions
double c_to_f(double c) { return (c * 9.0/5.0) + 32.0; }  // call-by-value
double f_to_c(double f) { return (f - 32.0) * 5.0/9.0; }  // call-by-value

int main(void) {
    double v; char unit;
    if (scanf("%lf %c", &v, &unit) != 2) return 0;
    if (unit == 'C' || unit == 'c') printf("%.2f", c_to_f(v)); else
    if (unit == 'F' || unit == 'f') printf("%.2f", f_to_c(v)); else
        printf("0.00"); // fallback for unexpected unit
    return 0;
}
```

---

If you want these exported to a **JSON/CSV** schema (e.g., `{title, difficulty, problem, input_format, output_format, tests[], solution}`), tell me the exact key names and I’ll produce a ready-to-import file.
Awesome — here are **10 LeetCode-style C problems on Functions (no recursion)** with real-world flavor. They cover **declaration/definition/invocation, call-by-value vs call-by-reference (pointers), scope (incl. static/local/global), and user-defined vs. library functions**.
Each problem has: a **single-paragraph statement**, **Input/Output formats**, **7 test cases** (first two include explanations), and a **full C solution**. No recursion anywhere.

---

### 1) Final Bill After Discount (Retail Checkout) — **Easy**

**Problem:**
At a retail counter, each bill has a gross amount and a discount percentage. Write a program that defines a function to compute the final bill as `gross - (gross * discount / 100)` using **call by value** and prints the final amount to two decimals.

**Input Format:**
Two numbers: `gross discount_percent`

**Output Format:**
Final amount to two decimals

**Test Cases:**

**1.**
**Input:**

```
1000 10
```

**Output:**

```
900.00
```

**Explanation:** 10% of 1000 is 100; 1000 − 100 = 900.

**2.**
**Input:**

```
799.99 12.5
```

**Output:**

```
699.99
```

**Explanation:** Discount = 99.99875 → final 699.99125 → prints 699.99.

**3.**
**Input:**

```
0 50
```

**Output:**

```
0.00
```

**4.**
**Input:**

```
250 0
```

**Output:**

```
250.00
```

**5.**
**Input:**

```
500 100
``**
Output:**
```

0.00

```

**6.**  
**Input:**
```

1234.56 1.2

```
**Output:**
```

1219.74

```

**7.**  
**Input:**
```

999.95 5

```
**Output:**
```

949.95

````

**Solution (C):**
```c
#include <stdio.h>

double final_amount(double gross, double disc) { // declaration + definition
    return gross - (gross * disc / 100.0);       // call-by-value
}

int main(void) {
    double g, d;
    if (scanf("%lf %lf", &g, &d) != 2) return 0;
    printf("%.2f", final_amount(g, d));          // invocation
    return 0;
}
````

---

### 2) Swap Seat Counts (Event Hall) — **Easy**

**Problem:**
Two sections of an event hall have interchanged seat counts in software due to a data entry mistake. Define a function that **swaps two integers via pointers (call by reference)** and print the corrected order.

**Input Format:**
Two integers: `A B`

**Output Format:**
`A B` after swap

**Test Cases:**

**1.**
**Input:**

```
120 300
```

**Output:**

```
300 120
```

**Explanation:** Values interchanged using pointer parameters.

**2.**
**Input:**

```
0 0
```

**Output:**

```
0 0
```

**Explanation:** Swapping equal zeroes stays zero.

**3.**
**Input:**

```
5 5
```

**Output:**

```
5 5
```

**4.**
**Input:**

```
-10 50
```

**Output:**

```
50 -10
```

**5.**
**Input:**

```
1 2
```

**Output:**

```
2 1
```

**6.**
**Input:**

```
999 -999
```

**Output:**

```
-999 999
```

**7.**
**Input:**

```
42 0
```

**Output:**

```
0 42
```

**Solution (C):**

```c
#include <stdio.h>

void swap_int(int *a, int *b) { int t = *a; *a = *b; *b = t; }

int main(void) {
    int a, b; if (scanf("%d %d", &a, &b) != 2) return 0;
    swap_int(&a, &b);
    printf("%d %d", a, b);
    return 0;
}
```

---

### 3) Apply Service Charge (Restaurant Bills) — **Easy**

**Problem:**
A restaurant system applies a uniform service charge percentage to every bill in a day. Define a function that takes an array of bill totals and updates each value **in place** using pointers (no recursion). Print the updated totals rounded to two decimals on one line separated by spaces.

**Input Format:**
`n`
`n` bill amounts (floats)
`charge_percent`

**Output Format:**
`n` updated amounts to two decimals (space-separated)

**Test Cases:**

**1.**
**Input:**

```
3
100 200 300
10
```

**Output:**

```
110.00 220.00 330.00
```

**Explanation:** +10% to each bill.

**2.**
**Input:**

```
4
50 75 25 100
0
```

**Output:**

```
50.00 75.00 25.00 100.00
```

**Explanation:** 0% keeps values same.

**3.**
**Input:**

```
1
99.99
5
```

**Output:**

```
104.99
```

**4.**
**Input:**

```
2
0 0
12
```

**Output:**

```
0.00 0.00
```

**5.**
**Input:**

```
5
10 20 30 40 50
-10
```

**Output:**

```
9.00 18.00 27.00 36.00 45.00
```

**6.**
**Input:**

```
3
1.11 2.22 3.33
50
```

**Output:**

```
1.67 3.33 5.00
```

**7.**
**Input:**

```
2
1000 0.01
1
```

**Output:**

```
1010.00 0.01
```

**Solution (C):**

```c
#include <stdio.h>

void apply_charge(double *arr, int n, double pct) {
    for (int i = 0; i < n; ++i) arr[i] += arr[i] * pct / 100.0;
}

int main(void) {
    int n; if (scanf("%d", &n) != 1) return 0;
    double a[200005];
    for (int i = 0; i < n; ++i) scanf("%lf", &a[i]);
    double p; scanf("%lf", &p);
    apply_charge(a, n, p);
    for (int i = 0; i < n; ++i) { if (i) printf(" "); printf("%.2f", a[i]); }
    return 0;
}
```

---

### 4) Safe Divide Orders (Warehouse Binning) — **Easy**

**Problem:**
A warehouse splits `total_items` evenly into boxes; any leftover is kept aside. Define a function that performs integer division safely without recursion: it should write the quotient and remainder to **output parameters** (pointers). Print `quotient remainder`.

**Input Format:**
`total_items boxes`

**Output Format:**
`quotient remainder`

**Test Cases:**

**1.**
**Input:**

```
100 6
```

**Output:**

```
16 4
```

**Explanation:** 100/6 = 16 remainder 4.

**2.**
**Input:**

```
9 3
```

**Output:**

```
3 0
```

**Explanation:** Exactly divisible.

**3.**
**Input:**

```
7 10
```

**Output:**

```
0 7
```

**4.**
**Input:**

```
0 5
```

**Output:**

```
0 0
```

**5.**
**Input:**

```
25 4
```

**Output:**

```
6 1
```

**6.**
**Input:**

```
-7 3
```

**Output:**

```
-2 -1
```

**7.**
**Input:**

```
7 -3
```

**Output:**

```
-2 1
```

**Solution (C):**

```c
#include <stdio.h>

void safe_divide(int a, int b, int *q, int *r) {
    if (b == 0) { *q = 0; *r = 0; return; }
    *q = a / b;
    *r = a % b; // C remainder keeps sign of dividend
}

int main(void) {
    int total, boxes; if (scanf("%d %d", &total, &boxes) != 2) return 0;
    int q, r; safe_divide(total, boxes, &q, &r);
    printf("%d %d", q, r);
    return 0;
}
```

---

### 5) Running Ticket IDs (Support Desk) — **Medium**

**Problem:**
A helpdesk assigns a new ticket ID each time a request is processed during the program run. Define a function `next_id()` with a **static local variable** that increases on every call, starting at 1. Given `n`, print the sequence of `n` ticket IDs separated by spaces.

**Input Format:**
`n`

**Output Format:**
`n` IDs (1-based, space-separated)

**Test Cases:**

**1.**
**Input:**

```
5
```

**Output:**

```
1 2 3 4 5
```

**Explanation:** Static variable persists across calls.

**2.**
**Input:**

```
1
```

**Output:**

```
1
```

**Explanation:** Only one ID requested.

**3.**
**Input:**

```
3
```

**Output:**

```
1 2 3
```

**4.**
**Input:**

```
0
```

**Output:**

```
```

**5.**
**Input:**

```
2
```

**Output:**

```
1 2
```

**6.**
**Input:**

```
7
```

**Output:**

```
1 2 3 4 5 6 7
```

**7.**
**Input:**

```
10
```

**Output:**

```
1 2 3 4 5 6 7 8 9 10
```

**Solution (C):**

```c
#include <stdio.h>

int next_id(void) { static int id = 0; id += 1; return id; } // scope demo

int main(void) {
    int n; if (scanf("%d", &n) != 1) return 0;
    for (int i = 0; i < n; ++i) { if (i) printf(" "); printf("%d", next_id()); }
    return 0;
}
```

---

### 6) Mask Email Username (Privacy Tool) — **Medium**

**Problem:**
For privacy display, show an email by keeping its first and last username characters and replacing the middle of the username (before `@`) with asterisks. Define a function that **modifies the string in place** using pointers and **library `<ctype.h>`** to normalize to lowercase for the username only. Print the masked email (domain unchanged).

**Input Format:**
One email string (no spaces)

**Output Format:**
Masked email

**Test Cases:**

**1.**
**Input:**

```
Alice.Wonder@Example.com
```

**Output:**

```
a**********r@Example.com
```

**Explanation:** Username `Alice.Wonder` → lowercased; keep first `a` and last `r`, mask middle.

**2.**
**Input:**

```
X@site.io
```

**Output:**

```
x@site.io
```

**Explanation:** Single-char username stays as is (no middle to mask).

**3.**
**Input:**

```
ab@d.com
```

**Output:**

```
ab@d.com
```

**4.**
**Input:**

```
abc@d.com
```

**Output:**

```
a*c@d.com
```

**5.**
**Input:**

```
john_doe@company.org
```

**Output:**

```
j*******e@company.org
```

**6.**
**Input:**

```
USER@DOMAIN.COM
```

**Output:**

```
u**r@DOMAIN.COM
```

**7.**
**Input:**

```
manydots...here@host.net
```

**Output:**

```
m**************e@host.net
```

**Solution (C):**

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void mask(char *s) {
    char *at = strchr(s, '@');
    if (!at) return;
    // lowercase username
    for (char *p = s; p < at; ++p) *p = (char)tolower((unsigned char)*p);
    int len = (int)(at - s);
    if (len <= 1) return;              // nothing to mask
    if (len == 2) return;              // keep both
    // mask middle
    for (int i = 1; i < len - 1; ++i) s[i] = '*';
}

int main(void) {
    char email[200005];
    if (scanf("%200000s", email) != 1) return 0;
    mask(email);
    printf("%s", email);
    return 0;
}
```

---

### 7) Product Key Validator (Manufacturing) — **Medium**

**Problem:**
A production line prints product keys like `AB12-CD34`. Define a function that checks if a key is valid: exactly 9 chars with a hyphen at position 5, all others alphanumeric (use **library `<ctype.h>`**). Print `Valid` or `Invalid`.

**Input Format:**
One product key (no spaces)

**Output Format:**
`Valid` or `Invalid`

**Test Cases:**

**1.**
**Input:**

```
AB12-CD34
```

**Output:**

```
Valid
```

**Explanation:** Matches pattern.

**2.**
**Input:**

```
a1b2c-d3e4
```

**Output:**

```
Valid
```

**Explanation:** Case and digits allowed; hyphen at position 5.

**3.**
**Input:**

```
AB12CD34
```

**Output:**

```
Invalid
```

**4.**
**Input:**

```
AB12-CD3@
```

**Output:**

```
Invalid
```

**5.**
**Input:**

```
----CD34
```

**Output:**

```
Invalid
```

**6.**
**Input:**

```
1234-5678
```

**Output:**

```
Valid
```

**7.**
**Input:**

```
A23--567
```

**Output:**

```
Invalid
```

**Solution (C):**

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int valid_key(const char *s) {
    if ((int)strlen(s) != 9) return 0;
    for (int i = 0; i < 9; ++i) {
        if (i == 4) { if (s[i] != '-') return 0; }
        else if (!isalnum((unsigned char)s[i])) return 0;
    }
    return 1;
}

int main(void) {
    char key[64];
    if (scanf("%63s", key) != 1) return 0;
    printf("%s", valid_key(key) ? "Valid" : "Invalid");
    return 0;
}
```

---

### 8) KPI Summary (Min/Max/Average) — **Hard**

**Problem:**
An operations dashboard needs a quick KPI summary from `n` daily metrics. Define **three user-defined functions**: `min_val`, `max_val`, and `avg_val` (all non-recursive). Read `n` integers, then print `min max avg` where avg is to two decimals.

**Input Format:**
`n`
`n` space-separated integers

**Output Format:**
`min max avg` (avg to two decimals)

**Test Cases:**

**1.**
**Input:**

```
5
10 20 30 40 50
```

**Output:**

```
10 50 30.00
```

**Explanation:** Min=10, Max=50, Avg=30.00.

**2.**
**Input:**

```
4
-1 -1 -1 -1
```

**Output:**

```
-1 -1 -1.00
```

**Explanation:** All equal negatives.

**3.**
**Input:**

```
1
7
```

**Output:**

```
7 7 7.00
```

**4.**
**Input:**

```
3
0 0 1
```

**Output:**

```
0 1 0.33
```

**5.**
**Input:**

```
6
5 4 3 2 1 0
```

**Output:**

```
0 5 2.50
```

**6.**
**Input:**

```
3
100 100 101
```

**Output:**

```
100 101 100.33
```

**7.**
**Input:**

```
5
-5 0 5 -10 10
```

**Output:**

```
-10 10 0.00
```

**Solution (C):**

```c
#include <stdio.h>

int min_val(const int *a, int n) { int m = a[0]; for (int i=1;i<n;++i) if (a[i]<m) m=a[i]; return m; }
int max_val(const int *a, int n) { int m = a[0]; for (int i=1;i<n;++i) if (a[i]>m) m=a[i]; return m; }
double avg_val(const int *a, int n){ long long s=0; for(int i=0;i<n;++i) s+=a[i]; return (double)s/n; }

int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    int a[200005]; for (int i=0;i<n;++i) scanf("%d",&a[i]);
    printf("%d %d %.2f", min_val(a,n), max_val(a,n), avg_val(a,n));
    return 0;
}
```

---

### 9) Case-Insensitive Compare (Usernames) — **Hard**

**Problem:**
During login, two usernames should be considered equal ignoring letter case. Write a **user-defined function** that compares two strings case-insensitively using `<ctype.h>` (convert both to lower or upper while comparing) and returns -1, 0, or 1. Print the result.

**Input Format:**
Two strings `u v` (no spaces)

**Output Format:**
`-1` if `u < v`, `0` if equal, `1` if `u > v` (case-insensitive)

**Test Cases:**

**1.**
**Input:**

```
Alice alice
```

**Output:**

```
0
```

**Explanation:** Same ignoring case.

**2.**
**Input:**

```
beta Alpha
```

**Output:**

```
1
```

**Explanation:** `"beta"` > `"alpha"` lexicographically ignoring case.

**3.**
**Input:**

```
aa aB
```

**Output:**

```
-1
```

**4.**
**Input:**

```
Z zzz
```

**Output:**

```
-1
```

**5.**
**Input:**

```
dev DEV
```

**Output:**

```
0
```

**6.**
**Input:**

```
longName short
```

**Output:**

```
1
```

**7.**
**Input:**

```
abc abd
```

**Output:**

```
-1
```

**Solution (C):**

```c
#include <stdio.h>
#include <ctype.h>

int ci_cmp(const char *a, const char *b) {
    while (*a && *b) {
        int ca = tolower((unsigned char)*a);
        int cb = tolower((unsigned char)*b);
        if (ca < cb) return -1;
        if (ca > cb) return 1;
        ++a; ++b;
        }
    if (*a) return 1;
    if (*b) return -1;
    return 0;
}

int main(void) {
    char u[200005], v[200005];
    if (scanf("%200000s %200000s", u, v) != 2) return 0;
    printf("%d", ci_cmp(u, v));
    return 0;
}
```

---

### 10) Temperature Conversion Menu (IoT Gateway) — **Hard**

**Problem:**
An IoT gateway receives a reading and a unit code. Create two **user-defined functions**: `c_to_f` and `f_to_c`. If unit is `C`, convert Celsius to Fahrenheit; if `F`, convert Fahrenheit to Celsius. Show **function declaration, definition, and invocation** clearly, and print the converted value to two decimals.

**Input Format:**
`value unit` (unit is `C` or `F`)

**Output Format:**
Converted value to two decimals

**Test Cases:**

**1.**
**Input:**

```
0 C
```

**Output:**

```
32.00
```

**Explanation:** 0°C → 32°F.

**2.**
**Input:**

```
212 F
```

**Output:**

```
100.00
```

**Explanation:** 212°F → 100°C.

**3.**
**Input:**

```
25 C
```

**Output:**

```
77.00
```

**4.**
**Input:**

```
98.6 F
```

**Output:**

```
37.00
```

**5.**
**Input:**

```
-40 C
```

**Output:**

```
-40.00
```

**6.**
**Input:**

```
451 F
```

**Output:**

```
232.78
```

**7.**
**Input:**

```
15 C
```

**Output:**

```
59.00
```

**Solution (C):**

```c
#include <stdio.h>

// declarations
double c_to_f(double c);
double f_to_c(double f);

// definitions
double c_to_f(double c) { return (c * 9.0/5.0) + 32.0; }  // call-by-value
double f_to_c(double f) { return (f - 32.0) * 5.0/9.0; }  // call-by-value

int main(void) {
    double v; char unit;
    if (scanf("%lf %c", &v, &unit) != 2) return 0;
    if (unit == 'C' || unit == 'c') printf("%.2f", c_to_f(v)); else
    if (unit == 'F' || unit == 'f') printf("%.2f", f_to_c(v)); else
        printf("0.00"); // fallback for unexpected unit
    return 0;
}
```

