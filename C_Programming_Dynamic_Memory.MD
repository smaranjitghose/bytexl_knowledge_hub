### 1) Dynamic Inventory Sum (Warehouse Intake) — **Easy**

**Problem:**
A warehouse intake system reads the number of arriving cartons and their unit counts. Allocate an integer array dynamically, store the counts, compute the total using pointer arithmetic, print the sum, and release the memory.

**Input Format:**
`n`
`n` space-separated integers (carton unit counts)

**Output Format:**
One integer: total units

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

**Explanation:** Sum 1+2+3+4+5 = 15.

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

**Explanation:** Handles negatives; total is 5.

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
#include <stdlib.h>
int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    int *a = (int*)malloc(sizeof(int)*n);
    for (int i=0;i<n;++i) scanf("%d", a+i);
    long long sum = 0; for (int *p=a; p<a+n; ++p) sum += *p;
    printf("%lld", sum);
    free(a);
    return 0;
}
```

---

### 2) Average Order Value (Retail Analytics) — **Easy**

**Problem:**
A retail dashboard must calculate the average value of `n` orders. Allocate with `calloc` to ensure zero-init, read `n` order amounts, compute average as a double via pointer traversal, print with two decimals, and free the memory.

**Input Format:**
`n`
`n` space-separated integers (order amounts)

**Output Format:**
`<average>` to 2 decimals

**Test Cases:**

**1.**
**Input:**

```
4
2 4 6 8
```

**Output:**

```
5.00
```

**Explanation:** (2+4+6+8)/4 = 5.00.

**2.**
**Input:**

```
3
-3 0 3
```

**Output:**

```
0.00
```

**Explanation:** Totals to 0.

**3.**
**Input:**

```
1
7
```

**Output:**

```
7.00
```

**4.**
**Input:**

```
2
5 6
```

**Output:**

```
5.50
```

**5.**
**Input:**

```
5
0 0 0 0 5
```

**Output:**

```
1.00
```

**6.**
**Input:**

```
2
100 -100
```

**Output:**

```
0.00
```

**7.**
**Input:**

```
3
1 2 2
```

**Output:**

```
1.67
```

**Solution (C):**

```c
#include <stdio.h>
#include <stdlib.h>
int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    int *a = (int*)calloc(n, sizeof(int));
    for (int i=0;i<n;++i) scanf("%d", a+i);
    long long s=0; for (int *p=a; p<a+n; ++p) s += *p;
    double avg = n ? (double)s/n : 0.0;
    printf("%.2f", avg);
    free(a);
    return 0;
}
```

---

### 3) Append Shipments (Log Growth with `realloc`) — **Easy**

**Problem:**
A logistics service stores shipment IDs in a dynamic array. Read an initial list, then append a second list by resizing with `realloc`. Print the final size and all IDs, then free memory.

**Input Format:**
`n`
`n` integers (initial IDs)
`m`
`m` integers (new IDs)

**Output Format:**
First line: `n+m`
Second line: `n+m` integers (space-separated)

**Test Cases:**

**1.**
**Input:**

```
3
1 2 3
2
4 5
```

**Output:**

```
5
1 2 3 4 5
```

**Explanation:** Appended 2 IDs.

**2.**
**Input:**

```
0

3
7 8 9
```

**Output:**

```
3
7 8 9
```

**Explanation:** Started empty.

**3.**
**Input:**

```
2
10 20
0
```

**Output:**

```
2
10 20
```

**4.**
**Input:**

```
1
-1
1
-2
```

**Output:**

```
2
-1 -2
```

**5.**
**Input:**

```
2
5 5
3
5 5 5
```

**Output:**

```
5
5 5 5 5 5
```

**6.**
**Input:**

```
1
100
1
-100
```

**Output:**

```
2
100 -100
```

**7.**
**Input:**

```
4
1 3 5 7
2
2 4
```

**Output:**

```
6
1 3 5 7 2 4
```

**Solution (C):**

```c
#include <stdio.h>
#include <stdlib.h>
int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    int *a = (int*)malloc(sizeof(int)*(n>0?n:1));
    for (int i=0;i<n;++i) scanf("%d",&a[i]);
    int m; scanf("%d",&m);
    a = (int*)realloc(a, sizeof(int)*(n+m));
    for (int i=0;i<m;++i) scanf("%d",&a[n+i]);
    printf("%d\n", n+m);
    for (int i=0;i<n+m;++i){ if(i) printf(" "); printf("%d", a[i]); }
    free(a);
    return 0;
}
```

---

### 4) Remove Defective SKU (Shrink with `realloc`) — **Easy**

**Problem:**
Quality control flags the `k`-th SKU in a batch for removal. Read `n` SKUs, remove the element at index `k` (0-based) by shifting, shrink the array with `realloc`, print the remaining SKUs, and free memory. If `k` is invalid, print an empty line.

**Input Format:**
`n`
`n` integers (SKUs)
`k`

**Output Format:**
`n-1` integers (space-separated) or empty line if invalid

**Test Cases:**

**1.**
**Input:**

```
5
10 20 30 40 50
2
```

**Output:**

```
10 20 40 50
```

**Explanation:** Removed SKU at index 2.

**2.**
**Input:**

```
3
1 2 3
0
```

**Output:**

```
2 3
```

**Explanation:** Removed first SKU.

**3.**
**Input:**

```
1
9
0
```

**Output:**

```
```

**4.**
**Input:**

```
4
5 6 7 8
3
```

**Output:**

```
5 6 7
```

**5.**
**Input:**

```
4
5 6 7 8
4
```

**Output:**

```
```

**6.**
**Input:**

```
2
-1 -2
1
```

**Output:**

```
-1
```

**7.**
**Input:**

```
5
0 0 0 1 0
3
```

**Output:**

```
0 0 0 0
```

**Solution (C):**

```c
#include <stdio.h>
#include <stdlib.h>
int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    int *a = (int*)malloc(sizeof(int)*(n>0?n:1));
    for (int i=0;i<n;++i) scanf("%d",&a[i]);
    int k; scanf("%d",&k);
    if (n>0 && k>=0 && k<n){
        for (int i=k;i<n-1;++i) a[i]=a[i+1];
        --n;
        a = (int*)realloc(a, sizeof(int)*(n>0?n:1));
        for (int i=0;i<n;++i){ if(i) printf(" "); printf("%d",a[i]); }
    } // invalid -> print empty line
    free(a);
    return 0;
}
```

---

### 5) Build Email Subject (Tokens with `char**` + `realloc`) — **Medium**

**Problem:**
An email composer receives `t` subject tokens (no spaces in a token). Store each word as a dynamically allocated string in a `char**`. Then build a single subject line by growing a dynamic `char*` buffer with `realloc`, inserting single spaces between words. Print the final subject and free all allocations.

**Input Format:**
`t`
`t` words (ASCII, no spaces)

**Output Format:**
One line: subject (tokens separated by one space)

**Test Cases:**

**1.**
**Input:**

```
3
urgent meeting today
```

**Output:**

```
urgent meeting today
```

**Explanation:** Joined with single spaces.

**2.**
**Input:**

```
1
reminder
```

**Output:**

```
reminder
```

**Explanation:** Single token.

**3.**
**Input:**

```
2
project update
```

**Output:**

```
project update
```

**4.**
**Input:**

```
4
a b c d
```

**Output:**

```
a b c d
```

**5.**
**Input:**

```
3
pointer to pointer
```

**Output:**

```
pointer to pointer
```

**6.**
**Input:**

```
2
C language
```

**Output:**

```
C language
```

**7.**
**Input:**

```
5
dynamic memory allocation in c
```

**Output:**

```
dynamic memory allocation in c
```

**Solution (C):**

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main(void){
    int t; if (scanf("%d",&t)!=1) return 0;
    char **words = (char**)malloc(sizeof(char*)*(t>0?t:1));
    for (int i=0;i<t;++i){
        char buf[1005]; scanf("%s", buf);
        size_t L = strlen(buf);
        words[i] = (char*)malloc(L+1);
        strcpy(words[i], buf);
    }
    char *out = NULL; size_t cap=0, len=0;
    for (int i=0;i<t;++i){
        size_t need = len + (i?1:0) + strlen(words[i]) + 1;
        if (need > cap){ cap = need*2; out = (char*)realloc(out, cap); }
        if (i) out[len++] = ' ';
        strcpy(out+len, words[i]); len += strlen(words[i]);
    }
    if (!out){ out = (char*)malloc(1); out[0]='\0'; }
    printf("%s", out);
    for (int i=0;i<t;++i) free(words[i]);
    free(words); free(out);
    return 0;
}
```

---

### 6) Jagged Store Sales (Ragged Rows with `int**` + `calloc`) — **Medium**

**Problem:**
A chain tracks daily sales per store with different item counts per store. Read `r`, then `r` row lengths, allocate an array of `int*` and each row via `calloc`, read values, compute each row’s sum using pointers, print all sums space-separated, and free memory.

**Input Format:**
`r`
`r` integers (row lengths)
Then for each row, `len[i]` integers

**Output Format:**
`r` integers (space-separated row sums)

**Test Cases:**

**1.**
**Input:**

```
3
2 3 1
1 2
3 4 5
9
```

**Output:**

```
3 12 9
```

**Explanation:** Row sums are 3, 12, 9.

**2.**
**Input:**

```
2
1 2
-5
10 10
```

**Output:**

```
-5 20
```

**Explanation:** Sums per store.

**3.**
**Input:**

```
1
3
0 0 0
```

**Output:**

```
0
```

**4.**
**Input:**

```
2
2 2
1 1
-1 -1
```

**Output:**

```
2 -2
```

**5.**
**Input:**

```
4
1 1 1 1
7
8
9
10
```

**Output:**

```
7 8 9 10
```

**6.**
**Input:**

```
3
3 0 2
1 2 3

4 6
```

**Output:**

```
6 0 10
```

**7.**
**Input:**

```
2
5 3
1 2 3 4 5
6 7 8
```

**Output:**

```
15 21
```

**Solution (C):**

```c
#include <stdio.h>
#include <stdlib.h>
int main(void){
    int r; if (scanf("%d",&r)!=1) return 0;
    int *len = (int*)malloc(sizeof(int)*r);
    for (int i=0;i<r;++i) scanf("%d",&len[i]);
    int **A = (int**)malloc(sizeof(int*)*r);
    for (int i=0;i<r;++i){
        int L = len[i]>0?len[i]:1;
        A[i] = (int*)calloc(L, sizeof(int));
        for (int j=0;j<len[i];++j) scanf("%d",&A[i][j]);
    }
    for (int i=0;i<r;++i){
        long long s=0; for (int *p=A[i]; p<A[i]+len[i]; ++p) s += *p;
        if (i) printf(" "); printf("%lld", s);
    }
    for (int i=0;i<r;++i) free(A[i]);
    free(A); free(len);
    return 0;
}
```

---

### 7) Floor Plan Grid Transpose (Facilities) — **Medium**

**Problem:**
A facilities app stores a floor plan as an `m x n` grid (integers). Allocate the grid with `int**`, read it, create an `n x m` transposed grid dynamically, print the transpose, and free all memory.

**Input Format:**
`m n`
`m` lines with `n` integers

**Output Format:**
`n` lines with `m` integers (transpose)

**Test Cases:**

**1.**
**Input:**

```
2 3
1 2 3
4 5 6
```

**Output:**

```
1 4
2 5
3 6
```

**Explanation:** Transposed layout.

**2.**
**Input:**

```
1 4
7 8 9 10
```

**Output:**

```
7
8
9
10
```

**Explanation:** Row becomes column.

**3.**
**Input:**

```
3 1
5
6
7
```

**Output:**

```
5 6 7
```

**4.**
**Input:**

```
2 2
1 1
2 2
```

**Output:**

```
1 2
1 2
```

**5.**
**Input:**

```
3 3
0 1 0
1 0 1
0 1 0
```

**Output:**

```
0 1 0
1 0 1
0 1 0
```

**6.**
**Input:**

```
2 1
-1
-2
```

**Output:**

```
-1 -2
```

**7.**
**Input:**

```
1 1
42
``**
Output:**
```

42

````

**Solution (C):**
```c
#include <stdio.h>
#include <stdlib.h>
int main(void){
    int m,n; if (scanf("%d %d",&m,&n)!=2) return 0;
    int **A = (int**)malloc(sizeof(int*)*m);
    for (int i=0;i<m;++i){
        A[i] = (int*)malloc(sizeof(int)*n);
        for (int j=0;j<n;++j) scanf("%d",&A[i][j]);
    }
    int **T = (int**)malloc(sizeof(int*)*n);
    for (int i=0;i<n;++i) T[i] = (int*)malloc(sizeof(int)*m);
    for (int i=0;i<m;++i) for (int j=0;j<n;++j) T[j][i] = A[i][j];
    for (int i=0;i<n;++i){
        for (int j=0;j<m;++j){ if (j) printf(" "); printf("%d", T[i][j]); }
        if (i<n-1) printf("\n");
    }
    for (int i=0;i<m;++i) free(A[i]); free(A);
    for (int i=0;i<n;++i) free(T[i]); free(T);
    return 0;
}
````

---

### 8) Unique Customer IDs (Growable Set with `realloc`) — **Hard**

**Problem:**
A CRM stream may repeat customer IDs. Maintain a dynamic list of unique IDs: for each input, linearly check if seen; if not, `realloc` to append. Preserve first-seen order. Print the unique IDs and free memory.

**Input Format:**
`n`
`n` integers (customer IDs)

**Output Format:**
Unique IDs (space-separated)

**Test Cases:**

**1.**
**Input:**

```
7
1 2 2 3 1 4 3
```

**Output:**

```
1 2 3 4
```

**Explanation:** Keep first time each ID appears.

**2.**
**Input:**

```
5
5 5 5 5 5
```

**Output:**

```
5
```

**Explanation:** Only one 5 remains.

**3.**
**Input:**

```
0
```

**Output:**

```
```

**4.**
**Input:**

```
4
-1 0 -1 0
```

**Output:**

```
-1 0
```

**5.**
**Input:**

```
6
1 2 3 4 5 6
```

**Output:**

```
1 2 3 4 5 6
```

**6.**
**Input:**

```
6
2 1 2 3 3 2
```

**Output:**

```
2 1 3
```

**7.**
**Input:**

```
8
0 0 1 1 2 2 3 3
```

**Output:**

```
0 1 2 3
```

**Solution (C):**

```c
#include <stdio.h>
#include <stdlib.h>
int seen(int *u, int m, int v){ for(int i=0;i<m;++i) if(u[i]==v) return 1; return 0; }
int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    int *uniq = NULL; int m = 0;
    for (int i=0;i<n;++i){
        int x; scanf("%d",&x);
        if (!seen(uniq,m,x)){
            uniq = (int*)realloc(uniq, sizeof(int)*(m+1));
            uniq[m++] = x;
        }
    }
    for (int i=0;i<m;++i){ if(i) printf(" "); printf("%d", uniq[i]); }
    free(uniq);
    return 0;
}
```

---

### 9) Web Log Line Reader (Streaming `char*` + `realloc`) — **Hard**

**Problem:**
A log collector must read an entire log line of unknown length from stdin until newline, growing a buffer via `realloc` as needed. Store the line without the trailing newline and echo it back. Handle empty lines too, then free.

**Input Format:**
A single line (may be empty)

**Output Format:**
The same line (no extra newline beyond standard print)

**Test Cases:**

**1.**
**Input:**

```
GET /health 200 OK
```

**Output:**

```
GET /health 200 OK
```

**Explanation:** Captured arbitrary length.

**2.**
**Input:**

```
```

**Output:**

```
```

**Explanation:** Empty line preserved.

**3.**
**Input:**

```
user=jane action=login
```

**Output:**

```
user=jane action=login
```

**4.**
**Input:**

```
id=42
```

**Output:**

```
id=42
```

**5.**
**Input:**

```
   leading spaces are fine
```

**Output:**

```
   leading spaces are fine
```

**6.**
**Input:**

```
trailing spaces are fine   
```

**Output:**

```
trailing spaces are fine   
```

**7.**
**Input:**

```
A very very very long message
```

**Output:**

```
A very very very long message
```

**Solution (C):**

```c
#include <stdio.h>
#include <stdlib.h>
int main(void){
    char *buf = NULL; size_t cap=0, len=0; int c;
    while ((c=getchar())!=EOF && c!='\n'){
        if (len+1 >= cap){ cap = cap? cap*2 : 16; buf = (char*)realloc(buf, cap); }
        buf[len++] = (char)c;
    }
    if (!buf) buf = (char*)malloc(1);
    buf[len] = '\0';
    printf("%s", buf);
    free(buf);
    return 0;
}
```

---

### 10) Shortlist Top URLs (Pointer-to-Pointer List) — **Hard**

**Problem:**
A crawler extracts `t` candidate URLs (tokens without spaces). Allocate a dynamic list `char**` to store them. Then filter to keep only the first `k` (truncate with `realloc` of the pointer array), print each URL on a single line, and free all strings and the list. If `k > t`, keep all.

**Input Format:**
`t k`
`t` lines each with one URL (no spaces)

**Output Format:**
`min(t,k)` lines: the kept URLs

**Test Cases:**

**1.**
**Input:**

```
3 2
a.com
b.com
c.com
```

**Output:**

```
a.com
b.com
```

**Explanation:** Kept first two.

**2.**
**Input:**

```
2 5
x.io
y.dev
```

**Output:**

```
x.io
y.dev
```

**Explanation:** k exceeds t, keep all.

**3.**
**Input:**

```
1 1
home.page
```

**Output:**

```
home.page
```

**4.**
**Input:**

```
4 0
a
b
c
d
```

**Output:**

```
```

**5.**
**Input:**

```
5 3
u1
u2
u3
u4
u5
```

**Output:**

```
u1
u2
u3
```

**6.**
**Input:**

```
3 1
K
L
M
```

**Output:**

```
K
```

**7.**
**Input:**

```
2 2
alpha
beta
```

**Output:**

```
alpha
beta
```

**Solution (C):**

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main(void){
    int t,k; if (scanf("%d %d",&t,&k)!=2) return 0;
    char **list = (char**)malloc(sizeof(char*)*(t>0?t:1));
    for (int i=0;i<t;++i){
        char buf[2048]; scanf("%s", buf);
        size_t L = strlen(buf);
        list[i] = (char*)malloc(L+1);
        strcpy(list[i], buf);
    }
    int keep = (k<t)?k:t;
    list = (char**)realloc(list, sizeof(char*)*(keep>0?keep:1));
    for (int i=0;i<keep;++i) printf("%s%s", list[i], (i<keep-1) ? "\n" : "");
    // free kept
    for (int i=0;i<keep;++i) free(list[i]);
    free(list);
    return 0;
}
```
