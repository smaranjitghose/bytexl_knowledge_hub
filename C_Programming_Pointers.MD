## 1) The Memory Inspector

A debugging tool needs to show the address of a variable to help you verify memory layout. Given an integer, display its **value** and the **memory address** where it’s stored, using a pointer.

**Input Format**

* One integer `x`.

**Output Format**

* Line 1: `Value: X`
* Line 2: `Address: Y` (print with `%p`)

**Test Cases**
1.
**Input:**

```
0
```

**Output:**

```
Value: 0
Address: 0x...
```

2.

**Input:**

```
5
```

**Output:**

```
Value: 5
Address: 0x...
```

3.

**Input:**

```
-10
```

**Output:**

```
Value: -10
Address: 0x...
```

4.

**Input:**

```
12345
```

**Output:**

```
Value: 12345
Address: 0x...
```

5.

**Input:**

```
999999
```

**Output:**

```
Value: 999999
Address: 0x...
```

6.

**Input:**

```
1
```

**Output:**

```
Value: 1
Address: 0x...
```

7.

**Input:**

```
-1
```

**Output:**

```
Value: -1
Address: 0x...
```

> Note: The exact pointer value differs per run/environment.

### C Solution

```c
#include <stdio.h>

int main(void) {
    int x;
    if (scanf("%d", &x) != 1) return 0;
    int *p = &x;
    printf("Value: %d\n", *p);
    printf("Address: %p", (void*)p);
    return 0;
}
```

---

## 2) The Memory Swapper

You’re simulating a register swap. Two integers are provided; swap their values **using pointers only**.

**Input Format**

* Two integers `a b`.

**Output Format**

* Two integers after swap: `a b`.

**Test Cases**
1.
**Input:**

```
1 2
```

**Output:**

```
2 1
```

2.

**Input:**

```
0 0
```

**Output:**

```
0 0
```

3.

**Input:**

```
-5 10
```

**Output:**

```
10 -5
```

4.

**Input:**

```
7 -7
```

**Output:**

```
-7 7
```

5.

**Input:**

```
100 200
```

**Output:**

```
200 100
```

6.

**Input:**

```
42 42
```

**Output:**

```
42 42
```

7.

**Input:**

```
-1 -2
```

**Output:**

```
-2 -1
```

### C Solution

```c
#include <stdio.h>
int main(void){
    int a,b; if (scanf("%d %d",&a,&b)!=2) return 0;
    int *p=&a,*q=&b, t=*p; *p=*q; *q=t;
    printf("%d %d", a, b);
    return 0;
}
```

---

## 3) The Number Mover

Given `n` and an array, print all elements **using pointer arithmetic** (no `a[i]`).

**Input Format**

* `n`
* `n` integers

**Output Format**

* All `n` integers, space-separated.

**Test Cases**
1.
**Input:**

```
5
1 2 3 4 5
```

**Output:**

```
1 2 3 4 5
```

2.

**Input:**

```
1
9
```

**Output:**

```
9
```

3.

**Input:**

```
3
-1 0 1
```

**Output:**

```
-1 0 1
```

4.

**Input:**

```
4
10 10 10 10
```

**Output:**

```
10 10 10 10
```

5.

**Input:**

```
6
3 2 1 6 5 4
```

**Output:**

```
3 2 1 6 5 4
```

6.

**Input:**

```
2
-5 -6
```

**Output:**

```
-5 -6
```

7.

**Input:**

```
7
0 1 0 1 0 1 0
```

**Output:**

```
0 1 0 1 0 1 0
```

### C Solution

```c
#include <stdio.h>
int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    int a[100000];
    for(int i=0;i<n;i++) scanf("%d",&a[i]);
    int *p=a;
    for(int i=0;i<n;i++,p++){
        if(i) printf(" ");
        printf("%d", *p);
    }
    return 0;
}
```

---

## 4) The Running Total (Pointer Traversal)

A performance monitor stores readings in an array. Traverse via a pointer and compute the **sum** (no indexing).

**Input Format**

* `n`
* `n` integers

**Output Format**

* Single integer: sum.

**Test Cases**
1.
**Input:**

```
5
1 2 3 4 5
```

**Output:**

```
15
```

2.

**Input:**

```
3
-1 -2 -3
```

**Output:**

```
-6
```

3.

**Input:**

```
4
0 0 0 0
```

**Output:**

```
0
```

4.

**Input:**

```
1
999
```

**Output:**

```
999
```

5.

**Input:**

```
6
5 10 15 20 25 30
```

**Output:**

```
105
```

6.

**Input:**

```
2
-5 5
```

**Output:**

```
0
```

7.

**Input:**

```
7
1 1 1 1 1 1 1
```

**Output:**

```
7
```

### C Solution

```c
#include <stdio.h>
int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    int a[100000];
    for(int i=0;i<n;i++) scanf("%d",&a[i]);
    long long sum=0;
    int *p=a, *end=a+n;
    while(p<end){ sum += *p; p++; }
    printf("%lld", sum);
    return 0;
}
```

---

## 5) Pointer vs Array Demonstrator

Show that an array name behaves like a pointer to its first element: print **first** and **last** element using pointer dereference and arithmetic (no indexing).

**Input Format**

* `n`
* `n` integers

**Output Format**

* Two integers: `first last`.

**Test Cases**
1.
**Input:**

```
5
10 20 30 40 50
```

**Output:**

```
10 50
```

2.

**Input:**

```
1
7
```

**Output:**

```
7 7
```

3.

**Input:**

```
3
-1 0 1
```

**Output:**

```
-1 1
```

4.

**Input:**

```
4
5 5 5 5
```

**Output:**

```
5 5
```

5.

**Input:**

```
6
2 4 6 8 10 12
```

**Output:**

```
2 12
```

6.

**Input:**

```
2
-9 9
```

**Output:**

```
-9 9
```

7.

**Input:**

```
7
3 2 1 0 1 2 3
```

**Output:**

```
3 3
```

### C Solution

```c
#include <stdio.h>
int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    int a[100000];
    for(int i=0;i<n;i++) scanf("%d",&a[i]);
    int *p = a;
    int *q = a + (n - 1);
    printf("%d %d", *p, *q);
    return 0;
}
```

---

## 6) Null Pointer Guard

Read a `flag`. If `0`, set pointer to `NULL` and print `Invalid access`. If `1`, point to a valid variable and print it.

**Input Format**

* One integer `flag` (0 or 1).
* If `flag=1`, the next line has an integer `x` to store and print.

**Output Format**

* If `flag=0`: `Invalid access`
* If `flag=1`: `Pointer is valid: X`

**Test Cases**
1.
**Input:**

```
0
```

**Output:**

```
Invalid access
```

2.

**Input:**

```
1
5
```

**Output:**

```
Pointer is valid: 5
```

3.

**Input:**

```
1
-10
```

**Output:**

```
Pointer is valid: -10
```

4.

**Input:**

```
0
```

**Output:**

```
Invalid access
```

5.

**Input:**

```
1
0
```

**Output:**

```
Pointer is valid: 0
```

6.

**Input:**

```
1
12345
```

**Output:**

```
Pointer is valid: 12345
```

7.

**Input:**

```
1
-1
```

**Output:**

```
Pointer is valid: -1
```

### C Solution

```c
#include <stdio.h>
int main(void){
    int flag; if (scanf("%d",&flag)!=1) return 0;
    int *p = NULL;
    int x;
    if (flag==0){
        printf("Invalid access");
    } else {
        if (scanf("%d",&x)!=1) return 0;
        p = &x;
        printf("Pointer is valid: %d", *p);
    }
    return 0;
}
```

---

## 7) Dynamic Sensor Reader (Simulated)

Given `n` readings, print only the **first `k`** using pointer increments to simulate moving through allocated memory.

**Input Format**

* `n k`
* `n` integers

**Output Format**

* First `k` integers, space-separated.
* If `k=0`, print nothing (empty output).

**Test Cases**
1.
**Input:**

```
5 3
10 20 30 40 50
```

**Output:**

```
10 20 30
```

2.

**Input:**

```
5 5
1 2 3 4 5
```

**Output:**

```
1 2 3 4 5
```

3.

**Input:**

```
5 0
9 8 7 6 5
```

**Output:**

```
```

4.

**Input:**

```
3 2
-1 -2 -3
```

**Output:**

```
-1 -2
```

5.

**Input:**

```
6 4
0 1 0 1 0 1
```

**Output:**

```
0 1 0 1
```

6.

**Input:**

```
1 1
42
```

**Output:**

```
42
```

7.

**Input:**

```
7 6
2 4 6 8 10 12 14
```

**Output:**

```
2 4 6 8 10 12
```

### C Solution

```c
#include <stdio.h>
int main(void){
    int n,k; if (scanf("%d %d",&n,&k)!=2) return 0;
    int a[100000];
    for(int i=0;i<n;i++) scanf("%d",&a[i]);
    if (k<0) k=0; if (k>n) k=n;
    int *p=a;
    for(int i=0;i<k;i++,p++){
        if(i) printf(" ");
        printf("%d", *p);
    }
    return 0;
}
```

---

## 8) The Memory Leak Demonstrator (Dangling Pointer)

Illustrate a **dangling pointer**: take the address of a variable inside a block and show that using that pointer after the block ends is unsafe. Do **not** dereference after scope; just print the pointer value and a warning.

**Input Format**

* No input.

**Output Format**

* Two lines:

  * Inside block: `Inside: value=V, addr=%p`
  * Outside block: `Outside: dangling pointer detected at %p (do not dereference)`

**Test Cases**
1.
**Input:**

```
```

**Output:**

```
Inside: value=123, addr=0x...
Outside: dangling pointer detected at 0x... (do not dereference)
```

2–7. *(Same pattern; addresses vary.)*

### C Solution

```c
#include <stdio.h>
int main(void){
    int *dangling = NULL;
    {
        int local = 123;
        dangling = &local;
        printf("Inside: value=%d, addr=%p\n", local, (void*)dangling);
    }
    /* local is out of scope here; dangling is invalid to dereference */
    printf("Outside: dangling pointer detected at %p (do not dereference)", (void*)dangling);
    return 0;
}
```

---

## 9) The Reversed Road

Given distances between waypoints, print them **in reverse** using a pointer that starts at the last element and moves backward.

**Input Format**

* `n`
* `n` integers

**Output Format**

* Elements in reverse order, space-separated.

**Test Cases**
1.
**Input:**

```
5
1 2 3 4 5
```

**Output:**

```
5 4 3 2 1
```

2.

**Input:**

```
1
7
```

**Output:**

```
7
```

3.

**Input:**

```
3
-1 0 1
```

**Output:**

```
1 0 -1
```

4.

**Input:**

```
4
10 10 10 10
```

**Output:**

```
10 10 10 10
```

5.

**Input:**

```
6
3 2 1 6 5 4
```

**Output:**

```
4 5 6 1 2 3
```

6.

**Input:**

```
2
-5 -6
```

**Output:**

```
-6 -5
```

7.

**Input:**

```
7
0 1 0 1 0 1 0
```

**Output:**

```
0 1 0 1 0 1 0
```

### C Solution

```c
#include <stdio.h>
int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    int a[100000];
    for(int i=0;i<n;i++) scanf("%d",&a[i]);
    int *p = a + (n - 1);
    for(int i=0;i<n;i++,p--){
        if(i) printf(" ");
        printf("%d", *p);
    }
    return 0;
}
```

---

## 10) Memory Offset Finder

Given an array and offset `k`, print the value at position `k` using pointer arithmetic (no indexing). If `k` is out of range, print `Invalid`.

**Input Format**

* `n k`
* `n` integers

**Output Format**

* If `0 ≤ k < n`: the integer at offset `k`
* Else: `Invalid`

**Test Cases**
1.
**Input:**

```
5 0
10 20 30 40 50
```

**Output:**

```
10
```

2.

**Input:**

```
5 4
10 20 30 40 50
```

**Output:**

```
50
```

3.

**Input:**

```
3 1
-1 0 1
```

**Output:**

```
0
```

4.

**Input:**

```
4 3
5 5 5 5
```

**Output:**

```
5
```

5.

**Input:**

```
6 5
2 4 6 8 10 12
```

**Output:**

```
12
```

6.

**Input:**

```
2 2
7 9
```

**Output:**

```
Invalid
```

7.

**Input:**

```
1 0
42
```

**Output:**

```
42
```

### C Solution

```c
#include <stdio.h>
int main(void){
    int n, k; if (scanf("%d %d",&n,&k)!=2) return 0;
    int a[100000];
    for(int i=0;i<n;i++) scanf("%d",&a[i]);
    if (k < 0 || k >= n) {
        printf("Invalid");
        return 0;
    }
    int *base = a;
    int *ptr = base + k;
    printf("%d", *ptr);
    return 0;
}
```

