### 1) Swap Shipment Weights — **Easy**

**Problem:**
Two parcel weights were recorded under the wrong labels. Using pointers, swap the two floating-point values so that each label ends up with the correct weight, and print the swapped values.

**Input Format:**
Two floats `a b`.

**Output Format:**
`<a_after_swap> <b_after_swap>` (each to 2 decimals)

**Test Cases:**

**1.**
**Input:**

```
10.50 7.25
```

**Output:**

```
7.25 10.50
```

**Explanation:** The values are swapped: first becomes 7.25, second becomes 10.50.

**2.**
**Input:**

```
-3.00 12.00
```

**Output:**

```
12.00 -3.00
```

**Explanation:** Works for negative/positive.

**3.**
**Input:**

```
0.00 0.00
```

**Output:**

```
0.00 0.00
```

**4.**
**Input:**

```
5.00 5.00
```

**Output:**

```
5.00 5.00
```

**5.**
**Input:**

```
99.99 -99.99
```

**Output:**

```
-99.99 99.99
```

**6.**
**Input:**

```
1.23 4.56
```

**Output:**

```
4.56 1.23
```

**7.**
**Input:**

```
100.00 0.01
```

**Output:**

```
0.01 100.00
```

**Solution (C):**

```c
#include <stdio.h>
int main(void) {
    float a, b;
    if (scanf("%f %f", &a, &b) != 2) return 0;
    float *p = &a, *q = &b, t = *p;
    *p = *q; *q = t;
    printf("%.2f %.2f", a, b);
    return 0;
}
```

---

### 2) Area of a Rhombus — **Easy**

**Problem:**
A design tool receives the diagonals of a rhombus and must compute its area using pointers. Use the formula `area = (d1 * d2) / 2` and print the result to two decimals followed by `CM`.

**Input Format:**
Two floats on separate lines: `d1`, `d2`.

**Output Format:**
`The area of a rhombus is <area> CM`

**Test Cases:**

**1.**
**Input:**

```
3
4
```

**Output:**

```
The area of a rhombus is 6.00 CM
```

**Explanation:** `(3*4)/2 = 6.00`.

**2.**
**Input:**

```
10
5
```

**Output:**

```
The area of a rhombus is 25.00 CM
```

**Explanation:** `(10*5)/2 = 25.00`.

**3.**
**Input:**

```
0
12
```

**Output:**

```
The area of a rhombus is 0.00 CM
```

**4.**
**Input:**

```
7.5
2.0
```

**Output:**

```
The area of a rhombus is 7.50 CM
```

**5.**
**Input:**

```
1
1
```

**Output:**

```
The area of a rhombus is 0.50 CM
```

**6.**
**Input:**

```
8.2
9.3
```

**Output:**

```
The area of a rhombus is 38.13 CM
```

**7.**
**Input:**

```
100
0.5
```

**Output:**

```
The area of a rhombus is 25.00 CM
```

**Solution (C):**

```c
#include <stdio.h>
int main(void) {
    double d1, d2;
    if (scanf("%lf", &d1) != 1) return 0;
    if (scanf("%lf", &d2) != 1) return 0;
    double *p = &d1, *q = &d2;
    double area = (*p) * (*q) / 2.0;
    printf("The area of a rhombus is %.2f CM", area);
    return 0;
}
```

---

### 3) Message Text Length — **Easy**

**Problem:**
An SMS gateway needs the exact length of a message (ASCII). Using only pointer traversal, count characters until the null terminator and print the length in the required format.

**Input Format:**
A single word string (ASCII).

**Output Format:**
`Text length - "<len>"`

**Test Cases:**

**1.**
**Input:**

```
Hello
```

**Output:**

```
Text length - "5"
```

**Explanation:** Five characters in “Hello”.

**2.**
**Input:**

```
byteXL
```

**Output:**

```
Text length - "6"
```

**Explanation:** Six characters.

**3.**
**Input:**

```
```

**Output:**

```
Text length - "0"
```

**4.**
**Input:**

```
A
```

**Output:**

```
Text length - "1"
```

**5.**
**Input:**

```
pointer123
```

**Output:**

```
Text length - "10"
```

**6.**
**Input:**

```
CProgramming
```

**Output:**

```
Text length - "12"
```

**7.**
**Input:**

```
test_case
```

**Output:**

```
Text length - "9"
```

**Solution (C):**

```c
#include <stdio.h>
int main(void) {
    char s[200005];
    if (!fgets(s, sizeof(s), stdin)) { printf("Text length - \"0\""); return 0; }
    char *p = s; size_t len = 0;
    while (*p && *p != '\n') { ++len; ++p; }
    printf("Text length - \"%zu\"", len);
    return 0;
}
```

---

### 4) Sum of Sensor Readings — **Easy**

**Problem:**
A production line emits `N` integer readings. Using pointer arithmetic, traverse the array and compute the total sum without using indexing.

**Input Format:**
`N`
`N` space-separated integers

**Output Format:**
One integer: the sum

**Test Cases:**

**1.**
**Input:**

```
5
1 2 3 4 5
```

**Output:**

```
15
```

**Explanation:** 1+2+3+4+5=15.

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

**Explanation:** -2+7+0=5.

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
int main(void) {
    int n; if (scanf("%d", &n) != 1) return 0;
    long long sum = 0;
    for (int i = 0; i < n; ++i) { int x; scanf("%d", &x); int *p = &x; sum += *p; }
    printf("%lld", sum);
    return 0;
}
```

---

### 5) Find Peak Temperature — **Medium**

**Problem:**
Given hourly temperature logs, move a pointer from start to end and determine the highest value observed, then print it.

**Input Format:**
`N`
`N` space-separated integers

**Output Format:**
One integer: the maximum value

**Test Cases:**

**1.**
**Input:**

```
5
10 25 8 36 12
```

**Output:**

```
36
```

**Explanation:** 36 is the largest in the list.

**2.**
**Input:**

```
4
-5 -2 -9 -1
```

**Output:**

```
-1
```

**Explanation:** -1 is the maximum among negatives.

**3.**
**Input:**

```
1
42
```

**Output:**

```
42
```

**4.**
**Input:**

```
6
7 7 7 7 7 7
```

**Output:**

```
7
```

**5.**
**Input:**

```
5
0 100 50 100 20
```

**Output:**

```
100
```

**6.**
**Input:**

```
3
-10 0 -3
```

**Output:**

```
0
```

**7.**
**Input:**

```
8
5 4 3 2 1 0 -1 -2
```

**Output:**

```
5
```

**Solution (C):**

```c
#include <stdio.h>
int main(void) {
    int n; if (scanf("%d", &n) != 1) return 0;
    int x; scanf("%d", &x);
    int *p = &x; int mx = *p;
    for (int i = 1; i < n; ++i) { scanf("%d", &x); p = &x; if (*p > mx) mx = *p; }
    printf("%d", mx);
    return 0;
}
```

---

### 6) Reverse a Log Line (In-Place) — **Medium**

**Problem:**
A diagnostics viewer needs a mirrored version of a log line. Using two pointers, reverse the given null-terminated string in place and print the final string.

**Input Format:**
A single line string (ASCII).

**Output Format:**
The reversed string

**Test Cases:**

**1.**
**Input:**

```
system reboot
```

**Output:**

```
toober metsys
```

**Explanation:** Entire string reversed.

**2.**
**Input:**

```
abcde
```

**Output:**

```
edcba
```

**Explanation:** First becomes last, etc.

**3.**
**Input:**

```
```

**Output:**

```
```

**4.**
**Input:**

```
A
```

**Output:**

```
A
```

**5.**
**Input:**

```
racecar
```

**Output:**

```
racecar
```

**6.**
**Input:**

```
pointers
```

**Output:**

```
sretniop
```

**7.**
**Input:**

```
123 456
```

**Output:**

```
654 321
```

**Solution (C):**

```c
#include <stdio.h>
int main(void) {
    char s[200005];
    if (!fgets(s, sizeof(s), stdin)) return 0;
    int len = 0; while (s[len] && s[len] != '\n') ++len;
    char *l = s, *r = s + (len ? len - 1 : 0);
    while (l < r) { char t = *l; *l = *r; *r = t; ++l; --r; }
    s[len] = '\0';
    printf("%s", s);
    return 0;
}
```

---

### 7) Merge Two Sorted Delivery Times — **Medium**

**Problem:**
Two courier feeds provide non-decreasing delivery estimates. Using three pointers, merge both arrays into a third array in non-decreasing order and print the merged sequence.

**Input Format:**
`n m`
`n` integers (sorted)
`m` integers (sorted)

**Output Format:**
`n+m` integers (sorted, space-separated)

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

**Explanation:** Standard two-way merge.

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

**Explanation:** Only the second array contributes.

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
#define MAXN 200000
int main(void) {
    int n, m; if (scanf("%d %d", &n, &m) != 2) return 0;
    int a[MAXN], b[MAXN];
    for (int i = 0; i < n; ++i) scanf("%d", &a[i]);
    for (int j = 0; j < m; ++j) scanf("%d", &b[j]);
    int i = 0, j = 0; int first = 1;
    while (i < n && j < m) {
        int v = (a[i] <= b[j]) ? a[i++] : b[j++];
        if (!first) printf(" ");
        printf("%d", v); first = 0;
    }
    while (i < n) { if (!first) printf(" "); printf("%d", a[i++]); first = 0; }
    while (j < m) { if (!first) printf(" "); printf("%d", b[j++]); first = 0; }
    return 0;
}
```

---

### 8) Average Speed from Trip Segments — **Hard**

**Problem:**
A vehicle tracker reports `k` segments of distance (km) and time (hours). Using pointers, sum distances and times and print overall average speed as `sum(dist)/sum(time)` to two decimals with `km/h`.

**Input Format:**
`k`
`k` doubles for distance
`k` doubles for time

**Output Format:**
`<value> km/h` (to 2 decimals)

**Test Cases:**

**1.**
**Input:**

```
3
10 20 30
0.5 1.0 1.5
```

**Output:**

```
20.00 km/h
```

**Explanation:** Total distance 60, total time 3.0 → 60/3 = 20.00.

**2.**
**Input:**

```
2
100 50
2 1
```

**Output:**

```
50.00 km/h
```

**Explanation:** (150)/(3) = 50.00.

**3.**
**Input:**

```
1
0
0.25
``**
Output:**
```

0.00 km/h

```

**4.**  
**Input:**
```

4
5 5 5 5
0.5 0.5 0.5 0.5

```
**Output:**
```

10.00 km/h

```

**5.**  
**Input:**
```

3
12.5 7.5 0
1.0 2.0 1.0

```
**Output:**
```

6.25 km/h

```

**6.**  
**Input:**
```

2
1 2
0.25 0.25

```
**Output:**
```

6.00 km/h

```

**7.**  
**Input:**
```

3
33.3 33.3 33.4
1 1 1

```
**Output:**
```

33.33 km/h

````

**Solution (C):**
```c
#include <stdio.h>
int main(void) {
    int k; if (scanf("%d", &k) != 1) return 0;
    double sd = 0.0, st = 0.0, x;
    for (int i = 0; i < k; ++i) { scanf("%lf", &x); double *p = &x; sd += *p; }
    for (int i = 0; i < k; ++i) { scanf("%lf", &x); double *p = &x; st += *p; }
    double avg = (st > 0.0) ? (sd / st) : 0.0;
    printf("%.2f km/h", avg);
    return 0;
}
````

---

### 9) Normalize Spaces in a Status Line — **Hard**

**Problem:**
A publishing pipeline must reduce consecutive spaces to a single space and remove leading/trailing spaces. Using read and write pointers, rewrite the string in place and print the cleaned line.

**Input Format:**
A line that may contain multiple spaces.

**Output Format:**
The cleaned line (no leading/trailing spaces, single spaces between words)

**Test Cases:**

**1.**
**Input:**

```
  launch   day   today  
```

**Output:**

```
launch day today
```

**Explanation:** Leading/trailing spaces removed; multiple spaces collapsed.

**2.**
**Input:**

```
hello     world
```

**Output:**

```
hello world
```

**Explanation:** Five spaces between words become one.

**3.**
**Input:**

```
 single 
```

**Output:**

```
single
```

**4.**
**Input:**

```
a   b    c
```

**Output:**

```
a b c
```

**5.**
**Input:**

```
    
```

**Output:**

```
```

**6.**
**Input:**

```
noextra
```

**Output:**

```
noextra
```

**7.**
**Input:**

```
  many   words   here   
```

**Output:**

```
many words here
```

**Solution (C):**

```c
#include <stdio.h>
int main(void) {
    char s[200005];
    if (!fgets(s, sizeof(s), stdin)) return 0;
    char *r = s, *w = s;
    while (*r == ' ') ++r; // skip leading
    while (*r && *r != '\n') {
        if (*r == ' ') {
            while (*r == ' ') ++r;          // collapse run
            if (*r && *r != '\n') *w++ = ' '; // keep one if more chars ahead
        } else {
            *w++ = *r++;
        }
    }
    if (w > s && *(w-1) == ' ') --w; // trim trailing
    *w = '\0';
    printf("%s", s);
    return 0;
}
```

---

### 10) Adjust Grayscale Brightness — **Hard**

**Problem:**
Given `n` grayscale pixel values (0–255) and an adjustment `delta`, use a pointer to walk the buffer, add `delta` to each pixel, clamp the result to `[0,255]`, and print the adjusted values.

**Input Format:**
`n delta`
`n` integers in `[0,255]`

**Output Format:**
`n` adjusted integers (space-separated)

**Test Cases:**

**1.**
**Input:**

```
5 40
10 0 200 250 255
```

**Output:**

```
50 40 240 255 255
```

**Explanation:** Each pixel +40; clamp at 255 where needed.

**2.**
**Input:**

```
4 -30
20 30 15 0
```

**Output:**

```
0 0 0 0
```

**Explanation:** Negative shift underflows to 0.

**3.**
**Input:**

```
3 0
5 128 250
```

**Output:**

```
5 128 250
```

**4.**
**Input:**

```
3 10
245 246 247
```

**Output:**

```
255 255 255
```

**5.**
**Input:**

```
1 -255
255
```

**Output:**

```
0
```

**6.**
**Input:**

```
6 5
1 2 3 4 5 6
```

**Output:**

```
6 7 8 9 10 11
```

**7.**
**Input:**

```
3 -5
4 5 6
```

**Output:**

```
0 0 1
```

**Solution (C):**

```c
#include <stdio.h>
int main(void) {
    int n, delta; if (scanf("%d %d", &n, &delta) != 2) return 0;
    int first = 1;
    for (int i = 0; i < n; ++i) {
        int v; scanf("%d", &v);
        int *p = &v; int adj = *p + delta;
        if (adj < 0) adj = 0; else if (adj > 255) adj = 255;
        if (!first) printf(" "); printf("%d", adj); first = 0;
    }
    return 0;
}
```

