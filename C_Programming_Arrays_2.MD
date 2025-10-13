## 1) Classroom Occupancy Map

Your college tracks classroom seating as a grid where `1` means an occupied seat and `0` means empty. Given a snapshot of a classroom’s seating map, report how many seats are occupied and how many are empty so facilities can plan cleaning and ventilation priorities.

**Input Format**

* First line: two integers `r c`
* Next `r` lines: each has `c` integers (0 or 1)

**Output Format**

* One line: `Occupied X Empty Y`

**Test Cases**
1.

```
2 3
1 0 1
0 1 0
```

Output:

```
Occupied 3 Empty 3
```

2.

```
1 4
0 0 0 0
```

Output:

```
Occupied 0 Empty 4
```

3.

```
3 1
1
1
1
```

Output:

```
Occupied 3 Empty 0
```

4.

```
2 2
0 1
1 1
```

Output:

```
Occupied 3 Empty 1
```

5.

```
3 3
0 0 0
0 0 0
0 0 0
```

Output:

```
Occupied 0 Empty 9
```

6.

```
3 3
1 1 1
1 1 1
1 1 1
```

Output:

```
Occupied 9 Empty 0
```

7.

```
2 5
1 0 0 1 0
0 0 1 0 1
```

Output:

```
Occupied 4 Empty 6
```

### C Solution

```c
#include <stdio.h>

int main() {
    int r, c, x;
    if (scanf("%d %d", &r, &c) != 2) return 0;
    int occ = 0, emp = 0;
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {
            scanf("%d", &x);
            if (x == 1) occ++; else emp++;
        }
    }
    printf("Occupied %d Empty %d", occ, emp);
    return 0;
}
```

---

## 2) Sensor Grid Merger (Matrix Addition)

Two environmental sensor grids recorded particulate levels at the same times but on different devices. For a fair estimate, combine them by adding the two grids cell-by-cell to produce a merged reading grid.

**Input Format**

* First line: `r c`
* Next `r` lines: matrix A
* Next `r` lines: matrix B (same dimensions)

**Output Format**

* The `r × c` matrix `A+B`, each row on a new line

**Test Cases**
1.

```
2 2
1 2
3 4
5 6
7 8
```

Output:

```
6 8
10 12
```

2.

```
1 3
0 0 0
1 2 3
```

Output:

```
1 2 3
```

3.

```
2 3
1 -1 2
0 5 7
-1 1 -2
3 0 -7
```

Output:

```
0 0 0
3 5 0
```

4.

```
3 1
10
20
30
-10
-5
5
```

Output:

```
0
15
35
```

5.

```
2 2
100 200
300 400
-100 -200
-300 -400
```

Output:

```
0 0
0 0
```

6.

```
2 3
1 2 3
4 5 6
6 5 4
3 2 1
```

Output:

```
7 7 7
7 7 7
```

7.

```
3 3
1 0 1
0 1 0
1 0 1
9 9 9
9 9 9
9 9 9
```

Output:

```
10 9 10
9 10 9
10 9 10
```

### C Solution

```c
#include <stdio.h>

int main() {
    int r, c;
    if (scanf("%d %d", &r, &c) != 2) return 0;
    int A[100][100], B[100][100];
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++)
            scanf("%d", &A[i][j]);
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++)
            scanf("%d", &B[i][j]);
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {
            if (j) printf(" ");
            printf("%d", A[i][j] + B[i][j]);
        }
        if (i < r - 1) printf("\n");
    }
    return 0;
}
```

---

## 3) Change Map (Matrix Subtraction)

A lab runs two trials over the same area and wants a change map showing how readings shifted from Trial-1 to Trial-2. Compute Trial-2 minus Trial-1 for each cell.

**Input Format**

* First line: `r c`
* Next `r` lines: matrix T1
* Next `r` lines: matrix T2

**Output Format**

* The `r × c` matrix `T2 − T1`, row by row

**Test Cases**
1.

```
2 2
1 2
3 4
2 3
4 5
```

Output:

```
1 1
1 1
```

2.

```
1 3
5 5 5
2 5 8
```

Output:

```
-3 0 3
```

3.

```
2 3
0 0 0
0 0 0
1 2 3
4 5 6
```

Output:

```
1 2 3
4 5 6
```

4.

```
3 1
10
10
10
10
9
11
```

Output:

```
0
-1
1
```

5.

```
2 2
-1 -2
-3 -4
-1 -1
-1 -1
```

Output:

```
0 1
2 3
```

6.

```
2 2
100 0
0 100
50 50
50 50
```

Output:

```
-50 50
50 -50
```

7.

```
3 3
1 2 3
4 5 6
7 8 9
9 8 7
6 5 4
3 2 1
```

Output:

```
8 6 4
2 0 -2
-4 -6 -8
```

### C Solution

```c
#include <stdio.h>

int main() {
    int r, c;
    if (scanf("%d %d", &r, &c) != 2) return 0;
    int A[100][100], B[100][100];
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++)
            scanf("%d", &A[i][j]);
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++)
            scanf("%d", &B[i][j]);
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {
            if (j) printf(" ");
            printf("%d", B[i][j] - A[i][j]);
        }
        if (i < r - 1) printf("\n");
    }
    return 0;
}
```

---

## 4) Floor Plan Reorientation (Transpose)

A building’s floor plan is stored as a square matrix where rows are corridors and columns are rooms. To align with another team’s orientation, produce the transpose so that rows become columns.

**Input Format**

* First line: `n`
* Next `n` lines: `n` integers each

**Output Format**

* The `n × n` transposed matrix

**Test Cases**
1.

```
2
1 2
3 4
```

Output:

```
1 3
2 4
```

2.

```
1
7
```

Output:

```
7
```

3.

```
3
0 1 2
3 4 5
6 7 8
```

Output:

```
0 3 6
1 4 7
2 5 8
```

4.

```
2
-1 10
20 -5
```

Output:

```
-1 20
10 -5
```

5.

```
3
1 0 0
0 1 0
0 0 1
```

Output:

```
1 0 0
0 1 0
0 0 1
```

6.

```
2
9 9
9 9
```

Output:

```
9 9
9 9
```

7.

```
3
2 -1 4
0 0 5
7 8 9
```

Output:

```
2 0 7
-1 0 8
4 5 9
```

### C Solution

```c
#include <stdio.h>

int main() {
    int n; 
    if (scanf("%d", &n) != 1) return 0;
    int A[100][100];
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            scanf("%d", &A[i][j]);
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            if (j) printf(" ");
            printf("%d", A[j][i]);
        }
        if (i < n - 1) printf("\n");
    }
    return 0;
}
```

---

## 5) Utility Billing Dashboard (Row & Column Totals)

A facilities dashboard shows hourly electricity usage for multiple labs: rows are labs, columns are hours. Compute the total consumption per lab and the total consumption per hour.

**Input Format**

* First line: `r c`
* Next `r` lines: usage matrix

**Output Format**

* Line 1: `r` integers — row sums (lab totals)
* Line 2: `c` integers — column sums (hour totals)

**Test Cases**
1.

```
2 3
1 2 3
4 5 6
```

Output:

```
6 15
5 7 9
```

2.

```
1 4
10 0 10 0
```

Output:

```
20
10 0 10 0
```

3.

```
3 1
5
-5
10
```

Output:

```
5 -5 10
10
```

4.

```
2 2
0 0
0 0
```

Output:

```
0 0
0 0
```

5.

```
3 3
1 1 1
2 2 2
3 3 3
```

Output:

```
3 6 9
6 6 6
```

6.

```
2 3
-1 -2 -3
3 2 1
```

Output:

```
-6 6
2 0 -2
```

7.

```
3 2
7 8
9 10
-1 -2
```

Output:

```
15 19 -3
15 16
```

### C Solution

```c
#include <stdio.h>

int main() {
    int r, c;
    if (scanf("%d %d", &r, &c) != 2) return 0;
    int A[100][100];
    long rowSum[100] = {0}, colSum[100] = {0};
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++) {
            scanf("%d", &A[i][j]);
            rowSum[i] += A[i][j];
            colSum[j] += A[i][j];
        }
    for (int i = 0; i < r; i++) {
        if (i) printf(" ");
        printf("%ld", rowSum[i]);
    }
    printf("\n");
    for (int j = 0; j < c; j++) {
        if (j) printf(" ");
        printf("%ld", colSum[j]);
    }
    return 0;
}
```

---

## 6) Contrast Stretch (Min–Shift Normalization)

An imaging tool stores intensity values in a grid. To improve contrast before display, shift the entire grid so the minimum value becomes `0` by subtracting the global minimum from every cell while preserving the data’s shape.

**Input Format**

* First line: `r c`
* Next `r` lines: intensity matrix

**Output Format**

* The normalized `r × c` matrix after subtracting the global minimum

**Test Cases**
1.

```
2 2
5 7
3 9
```

Output:

```
2 4
0 6
```

2.

```
1 3
0 -1 4
```

Output:

```
1 0 5
```

3.

```
2 3
-5 -5 -5
-5 -5 -5
```

Output:

```
0 0 0
0 0 0
```

4.

```
3 1
10
0
-10
```

Output:

```
20
10
0
```

5.

```
2 2
100 50
60 50
```

Output:

```
50 0
10 0
```

6.

```
2 3
3 2 1
6 5 4
```

Output:

```
2 1 0
5 4 3
```

7.

```
3 3
0 2 0
2 1 2
0 2 3
```

Output:

```
0 2 0
2 1 2
0 2 3
```

### C Solution

```c
#include <stdio.h>

int main() {
    int r, c;
    if (scanf("%d %d", &r, &c) != 2) return 0;
    int A[100][100];
    int mn = 0, first = 1;
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++) {
            scanf("%d", &A[i][j]);
            if (first) { mn = A[i][j]; first = 0; }
            else if (A[i][j] < mn) mn = A[i][j];
        }
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {
            if (j) printf(" ");
            printf("%d", A[i][j] - mn);
        }
        if (i < r - 1) printf("\n");
    }
    return 0;
}
```

---

## 7) Systems Check: Upper-Triangular Matrix

A square matrix from a dependency graph is expected to be upper-triangular, meaning every entry below the main diagonal is zero. Verify this property to ensure there are no backward dependencies in the build.

**Input Format**

* First line: `n`
* Next `n` lines: the matrix

**Output Format**

* Print `YES` if all elements below the main diagonal are `0`, else `NO`

**Test Cases**
1.

```
2
1 2
0 3
```

Output:

```
YES
```

2.

```
2
1 0
5 1
```

Output:

```
NO
```

3.

```
3
1 2 3
0 4 5
0 0 6
```

Output:

```
YES
```

4.

```
3
0 0 0
0 0 0
1 0 0
```

Output:

```
NO
```

5.

```
1
9
```

Output:

```
YES
```

6.

```
3
2 -1 7
0 3 5
0 0 0
```

Output:

```
YES
```

7.

```
3
1 2 3
0 0 4
0 5 6
```

Output:

```
NO
```

### C Solution

```c
#include <stdio.h>

int main() {
    int n;
    if (scanf("%d", &n) != 1) return 0;
    int x;
    int ok = 1;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            scanf("%d", &x);
            if (i > j && x != 0) ok = 0;
        }
    }
    printf("%s", ok ? "YES" : "NO");
    return 0;
}
```

---

## 8) Saddle Point Detector

A manufacturing grid lists defect probabilities. A **saddle point** is a cell that is the minimum in its row but the maximum in its column. Detect whether such a point exists; if multiple exist, any one is sufficient to confirm risk concentration.

**Input Format**

* First line: `r c`
* Next `r` lines: the matrix

**Output Format**

* If a saddle point exists, print its value; otherwise print `Not Found`

**Test Cases**
1.

```
3 3
1 2 3
3 1 2
2 3 1
```

Output:

```
Not Found
```

2.

```
3 3
3 1 2
4 5 0
6 2 1
```

Output:

```
Not Found
```

3.

```
2 2
1 4
3 2
```

Output:

```
Not Found
```

4.

```
3 3
1 3 2
5 4 6
7 8 9
```

Output:

```
7
```

5.

```
3 3
9 8 7
6 5 4
3 2 1
```

Output:

```
7
```

6.

```
2 3
2 2 2
2 2 2
```

Output:

```
2
```

7.

```
3 2
-1 0
-2 -3
-3 -2
```

Output:

```
-1
```

### C Solution

```c
#include <stdio.h>

int main() {
    int r, c;
    if (scanf("%d %d", &r, &c) != 2) return 0;
    int A[100][100];
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++)
            scanf("%d", &A[i][j]);

    for (int i = 0; i < r; i++) {
        int minVal = A[i][0], minCol = 0;
        for (int j = 1; j < c; j++) {
            if (A[i][j] < minVal) { minVal = A[i][j]; minCol = j; }
        }
        int isMaxInCol = 1;
        for (int k = 0; k < r; k++) {
            if (A[k][minCol] > minVal) { isMaxInCol = 0; break; }
        }
        if (isMaxInCol) {
            printf("%d", minVal);
            return 0;
        }
    }
    printf("Not Found");
    return 0;
}
```

---

## 9) Timetable Composition (Matrix Multiplication)

Two scheduling tables must be combined: the first (`A`) maps courses to time-blocks, the second (`B`) maps time-blocks to available rooms. Their product `C = A × B` maps courses directly to rooms using the standard triple-loop multiplication.

**Input Format**

* First line: `r1 c1`
* Next `r1` lines: matrix A
* Next line: `r2 c2`
* Next `r2` lines: matrix B
* (Guaranteed that `c1 == r2`)

**Output Format**

* The `r1 × c2` product matrix, row by row

**Test Cases**
1.

```
2 3
1 2 3
4 5 6
3 2
7 8
9 10
11 12
```

Output:

```
58 64
139 154
```

2.

```
1 2
2 3
2 1
4
5
```

Output:

```
23
```

3.

```
2 2
1 0
0 1
2 2
5 6
7 8
```

Output:

```
5 6
7 8
```

4.

```
2 2
2 2
2 2
2 2
1 0
0 1
```

Output:

```
2 2
2 2
```

5.

```
3 1
1
2
3
1 3
4 5 6
```

Output:

```
4 5 6
8 10 12
12 15 18
```

6.

```
1 3
0 0 0
3 2
1 2
3 4
0 5
```

Output:

```
0 0
```

7.

```
2 2
-1 2
3 -4
2 2
5 -6
-7 8
```

Output:

```
-19 22
43 -50
```

### C Solution

```c
#include <stdio.h>

int main() {
    int r1, c1, r2, c2;
    if (scanf("%d %d", &r1, &c1) != 2) return 0;
    int A[100][100], B[100][100], C[100][100];
    for (int i = 0; i < r1; i++)
        for (int j = 0; j < c1; j++)
            scanf("%d", &A[i][j]);
    if (scanf("%d %d", &r2, &c2) != 2) return 0;
    for (int i = 0; i < r2; i++)
        for (int j = 0; j < c2; j++)
            scanf("%d", &B[i][j]);

    for (int i = 0; i < r1; i++) {
        for (int j = 0; j < c2; j++) {
            long sum = 0;
            for (int k = 0; k < c1; k++) sum += (long)A[i][k] * B[k][j];
            C[i][j] = (int)sum;
        }
    }
    for (int i = 0; i < r1; i++) {
        for (int j = 0; j < c2; j++) {
            if (j) printf(" ");
            printf("%d", C[i][j]);
        }
        if (i < r1 - 1) printf("\n");
    }
    return 0;
}
```

---

## 10) Spiral Display for QA (Clockwise)

Quality auditors prefer reading grids in a **spiral order** (clockwise, starting at the top-left) to spot anomalies. Given a matrix, print its elements in the exact spiral traversal sequence so they can scan linearly.

**Input Format**

* First line: `r c`
* Next `r` lines: the matrix

**Output Format**

* One line: all elements in clockwise spiral order, space-separated

**Test Cases**
1.

```
2 3
1 2 3
4 5 6
```

Output:

```
1 2 3 6 5 4
```

2.

```
3 3
1 2 3
4 5 6
7 8 9
```

Output:

```
1 2 3 6 9 8 7 4 5
```

3.

```
1 4
9 8 7 6
```

Output:

```
9 8 7 6
```

4.

```
4 1
1
2
3
4
```

Output:

```
1 2 3 4
```

5.

```
3 4
1 2 3 4
5 6 7 8
9 10 11 12
```

Output:

```
1 2 3 4 8 12 11 10 9 5 6 7
```

6.

```
2 2
0 -1
-2 -3
```

Output:

```
0 -1 -3 -2
```

7.

```
3 2
1 2
3 4
5 6
```

Output:

```
1 2 4 6 5 3
```

### C Solution

```c
#include <stdio.h>

int main() {
    int r, c;
    if (scanf("%d %d", &r, &c) != 2) return 0;
    int A[100][100];
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++)
            scanf("%d", &A[i][j]);

    int top = 0, bottom = r - 1, left = 0, right = c - 1;
    int printed = 0, total = r * c;

    while (top <= bottom && left <= right) {
        for (int j = left; j <= right && printed < total; j++, printed++) {
            if (printed) printf(" ");
            printf("%d", A[top][j]);
        }
        top++;
        for (int i = top; i <= bottom && printed < total; i++, printed++) {
            if (printed) printf(" ");
            printf("%d", A[i][right]);
        }
        right--;
        for (int j = right; j >= left && top <= bottom && printed < total; j--, printed++) {
            if (printed) printf(" ");
            printf("%d", A[bottom][j]);
        }
        bottom--;
        for (int i = bottom; i >= top && left <= right && printed < total; i--, printed++) {
            if (printed) printf(" ");
            printf("%d", A[i][left]);
        }
        left++;
    }
    return 0;
}
```
