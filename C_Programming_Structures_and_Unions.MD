### 1) Earliest Booking Date (Struct Comparison) — **Easy**

**Problem:**
Travel agencies often receive bookings from multiple partner sites where date formats vary, but the internal system needs the earliest booking to prioritize hotel inventory. Each booking arrives as three integers: day, month, and year. Dates may span multiple years, and you must handle ties at the month and day level. Create a `Date` structure to hold `d`, `m`, and `y`. Read `n` dates, compare them chronologically, and print the earliest as `DD-MM-YYYY` with zero-padding.

**Input Format:**
`n`
Then `n` lines: `d m y`

**Output Format:**
`DD-MM-YYYY` (earliest)

**Test Cases:**

1. **Explanation:** 2024 < 2025, so 15-08-2024 is earliest.
   **Input:**

```
3
1 7 2025
30 6 2025
15 8 2024
```

**Output:**

```
15-08-2024
```

2. **Explanation:** Same year/month; day 9 is earlier than 10.
   **Input:**

```
2
10 1 2023
9 1 2023
```

**Output:**

```
09-01-2023
```

3.

**Input:**

```
1
31 12 2020
```

**Output:**

```
31-12-2020
```

4.

**Input:**

```
4
1 1 2022
1 1 2021
1 1 2023
1 1 2024
```

**Output:**

```
01-01-2021
```

5.

**Input:**

```
3
28 2 2020
29 2 2020
1 3 2020
```

**Output:**

```
28-02-2020
```

6.

**Input:**

```
2
31 1 2022
1 2 2021
```

**Output:**

```
01-02-2021
```

7.

**Input:**

```
3
5 5 2019
5 5 2018
5 5 2020
```

**Output:**

```
05-05-2018
```

**Solution (C):**

```c
#include <stdio.h>

typedef struct { int d, m, y; } Date;

int earlier(Date a, Date b){
    if (a.y != b.y) return a.y < b.y;
    if (a.m != b.m) return a.m < b.m;
    return a.d < b.d;
}

int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    Date best;
    for (int i=0;i<n;++i){
        Date t; scanf("%d %d %d",&t.d,&t.m,&t.y);
        if (i==0 || earlier(t,best)) best = t;
    }
    printf("%02d-%02d-%04d", best.d, best.m, best.y);
    return 0;
}
```

---

### 2) Student Report (Average & Grade) — **Easy**

**Problem:**
A school’s grading utility compiles an individual report by averaging three exam scores and assigning a final letter grade. Define a `Student` with `name` and three integer scores. Compute the average `(a+b+c)/3.0`, map to `A(>=90)`, `B(>=80)`, `C(>=70)`, `D(>=60)`, else `F`, and print `name avg grade`.

**Input Format:**
`name` (no spaces)
`a b c`

**Output Format:**
`<name> <avg_to_2dp> <grade_char>`

**Test Cases:**

1. **Explanation:** Avg = 90.00 → A.
   **Input:**

```
Riya
90 95 85
```

**Output:**

```
Riya 90.00 A
```

2. **Explanation:** Avg in [70,80) → C.
   **Input:**

```
Sam
70 75 72
```

**Output:**

```
Sam 72.33 C
```

3.

**Input:**

```
Kai
100 100 100
```

**Output:**

```
Kai 100.00 A
```

4.

**Input:**

```
Jo
60 60 60
```

**Output:**

```
Jo 60.00 D
```

5.

**Input:**

```
Ava
59 59 59
```

**Output:**

```
Ava 59.00 F
```

6.

**Input:**

```
Lee
80 80 80
```

**Output:**

```
Lee 80.00 B
```

7.

**Input:**

```
Mo
89 90 91
```

**Output:**

```
Mo 90.00 A
```

**Solution (C):**

```c
#include <stdio.h>

typedef struct { char name[64]; int a,b,c; } Student;

int main(void){
    Student s;
    if (scanf("%63s", s.name)!=1) return 0;
    scanf("%d %d %d", &s.a, &s.b, &s.c);
    double avg = (s.a + s.b + s.c)/3.0;
    char g = (avg>=90)?'A':(avg>=80)?'B':(avg>=70)?'C':(avg>=60)?'D':'F';
    printf("%s %.2f %c", s.name, avg, g);
    return 0;
}
```

---

### 3) Salary Update (Call-by-Reference with Struct) — **Easy**

**Problem:**
HR applies a percentage hike to an employee’s salary and downstream systems must see the update at the same memory location. Define `Emp { int id; double sal; double hike; }`, update salary **in place** via a pointer, then print `id new_salary` to two decimals.

**Input Format:**
`id`
`sal hike_percent`

**Output Format:**
`<id> <new_salary_to_2dp>`

**Test Cases:**

1. **Explanation:** +10% of 50000 → 55000.
   **Input:**

```
101
50000 10
```

**Output:**

```
101 55000.00
```

2. **Explanation:** 0% keeps same.
   **Input:**

```
7
30000 0
```

**Output:**

```
7 30000.00
```

3.

**Input:**

```
5
10000 100
```

**Output:**

```
5 20000.00
```

4.

**Input:**

```
3
25000 5
```

**Output:**

```
3 26250.00
```

5.

**Input:**

```
9
1 10
```

**Output:**

```
9 1.10
```

6.

**Input:**

```
11
99999.99 0.5
```

**Output:**

```
11 100499.99
```

7.

**Input:**

```
12
12345 12.5
```

**Output:**

```
12 13888.12
```

**Solution (C):**

```c
#include <stdio.h>

typedef struct { int id; double sal; double hike; } Emp;

void apply_hike(Emp *e){ e->sal += e->sal * (e->hike/100.0); }

int main(void){
    Emp e;
    scanf("%d", &e.id);
    scanf("%lf %lf", &e.sal, &e.hike);
    apply_hike(&e);
    printf("%d %.2f", e.id, e.sal);
    return 0;
}
```

---

### 4) Nearest Point to Origin (Struct & Function) — **Easy**

**Problem:**
A mapping service ranks two candidate points by proximity to the origin. Define `Point { double x,y; }`, compare squared distances, and in a tie choose the first. Print the winning point as `x y` to two decimals.

**Input Format:**
`x1 y1`
`x2 y2`

**Output Format:**
`<x y>` (closer point)

**Test Cases:**

1. **Explanation:** Distances 5 vs √2 → second is closer.
   **Input:**

```
3 4
1 1
```

**Output:**

```
1.00 1.00
```

2. **Explanation:** Both distance 2; choose first.
   **Input:**

```
-2 0
2 0
```

**Output:**

```
-2.00 0.00
```

3.

**Input:**

```
0 0
5 5
```

**Output:**

```
0.00 0.00
```

4.

**Input:**

```
-1 -1
-2 -2
```

**Output:**

```
-1.00 -1.00
```

5.

**Input:**

```
10 0
0 10
```

**Output:**

```
10.00 0.00
```

6.

**Input:**

```
1.5 1.5
1.5 2.0
```

**Output:**

```
1.50 1.50
```

7.

**Input:**

```
-3 4
-4 3
```

**Output:**

```
-3.00 4.00
```

**Solution (C):**

```c
#include <stdio.h>

typedef struct { double x,y; } Point;

double d2(Point p){ return p.x*p.x + p.y*p.y; }

int main(void){
    Point a,b; scanf("%lf %lf",&a.x,&a.y); scanf("%lf %lf",&b.x,&b.y);
    if (d2(a) <= d2(b)) printf("%.2f %.2f", a.x, a.y);
    else               printf("%.2f %.2f", b.x, b.y);
    return 0;
}
```

---

### 5) Add Durations (Normalize Time) — **Medium**

**Problem:**
A video editor merges two clip durations. After addition, seconds/minutes may overflow 59 and must be carried forward. Use `Time { int h,m,s; }`, normalize to `HH:MM:SS` with zero padding.

**Input Format:**
`h1 m1 s1`
`h2 m2 s2`

**Output Format:**
`HH:MM:SS` (normalized sum)

**Test Cases:**

1. **Explanation:** 40+30=70s → +1m10s; 59+0+1=60 → +1h0m.
   **Input:**

```
0 59 40
0 0 30
```

**Output:**

```
01:00:10
```

2. **Explanation:** Carry minutes/seconds.
   **Input:**

```
1 30 30
2 40 40
```

**Output:**

```
04:11:10
```

3.

**Input:**

```
0 0 0
0 0 0
```

**Output:**

```
00:00:00
```

4.

**Input:**

```
10 59 59
0 0 1
```

**Output:**

```
11:00:00
```

5.

**Input:**

```
5 20 50
3 39 15
```

**Output:**

```
08:00:05
```

6.

**Input:**

```
12 0 30
0 59 40
```

**Output:**

```
13:00:10
```

7.

**Input:**

```
0 30 30
0 30 30
```

**Output:**

```
01:01:00
```

**Solution (C):**

```c
#include <stdio.h>

typedef struct { int h,m,s; } Time;

int main(void){
    Time a,b; scanf("%d %d %d",&a.h,&a.m,&a.s); scanf("%d %d %d",&b.h,&b.m,&b.s);
    Time r; r.s = a.s + b.s; r.m = a.m + b.m; r.h = a.h + b.h;
    r.m += r.s / 60; r.s %= 60;
    r.h += r.m / 60; r.m %= 60;
    printf("%02d:%02d:%02d", r.h, r.m, r.s);
    return 0;
}
```

---

### 6) Contact Book (Array of Structs & Search) — **Medium**

**Problem:**
A CRM snapshot is kept in memory for quick lookups. Given a list of contacts and a query name (case-sensitive), print the phone if found; else `Not Found`. Use `Contact { char name[32]; char phone[16]; }`.

**Input Format:**
`n`
`n` lines: `<name> <phone>`
`queryName`

**Output Format:**
Phone or `Not Found`

**Test Cases:**

1. **Explanation:** Sam is present.
   **Input:**

```
3
Riya 99999
Sam 12345
Kai 55555
Sam
```

**Output:**

```
12345
```

2. **Explanation:** Jo not in list.
   **Input:**

```
2
Ava 111
Mo 222
Jo
```

**Output:**

```
Not Found
```

3.

**Input:**

```
1
X 7
X
```

**Output:**

```
7
```

4.

**Input:**

```
2
x 1
X 2
x
```

**Output:**

```
1
```

5.

**Input:**

```
3
A 1
B 2
C 3
C
```

**Output:**

```
3
```

6.

**Input:**

```
2
AA 10
AB 20
AA
```

**Output:**

```
10
```

7.

**Input:**

```
4
Tom 1
Tim 2
Tam 3
Tem 4
Tem
```

**Output:**

```
4
```

**Solution (C):**

```c
#include <stdio.h>
#include <string.h>

typedef struct { char name[32]; char phone[16]; } Contact;

int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    Contact a[1005];
    for (int i=0;i<n;++i) scanf("%31s %15s", a[i].name, a[i].phone);
    char q[32]; scanf("%31s", q);
    for (int i=0;i<n;++i) if (strcmp(a[i].name,q)==0){ printf("%s", a[i].phone); return 0; }
    printf("Not Found");
    return 0;
}
```

---

### 7) Sort Products by Price (Array of Structs) — **Medium**

**Problem:**
An inventory dashboard must present products in ascending price; ties break by name. Define `Product { char name[32]; double price; }`, sort, then print `name price` per line (two decimals).

**Input Format:**
`n`
`n` lines: `<name> <price>`

**Output Format:**
`n` lines: `<name> <price_to_2dp>` (sorted)

**Test Cases:**

1. **Explanation:** Sorted by price.
   **Input:**

```
3
Pen 10
Book 50
Ink 20
```

**Output:**

```
Pen 10.00
Ink 20.00
Book 50.00
```

2. **Explanation:** Tie at 5 → A before B.
   **Input:**

```
3
A 5
B 5
C 4
```

**Output:**

```
C 4.00
A 5.00
B 5.00
```

3.

**Input:**

```
1
Only 1
```

**Output:**

```
Only 1.00
```

4.

**Input:**

```
2
Z 9.99
Y 9.99
```

**Output:**

```
Y 9.99
Z 9.99
```

5.

**Input:**

```
4
p 2
q 1
r 3
s 0.5
```

**Output:**

```
s 0.50
q 1.00
p 2.00
r 3.00
```

6.

**Input:**

```
2
aa 10
a 10
```

**Output:**

```
a 10.00
aa 10.00
```

7.

**Input:**

```
3
x 1.11
y 1.10
z 1.12
```

**Output:**

```
y 1.10
x 1.11
z 1.12
```

**Solution (C):**

```c
#include <stdio.h>
#include <string.h>

typedef struct { char name[32]; double price; } Product;

int cmp(Product a, Product b){
    if (a.price < b.price) return -1;
    if (a.price > b.price) return  1;
    return strcmp(a.name, b.name);
}

int main(void){
    int n; if (scanf("%d",&n)!=1) return 0;
    Product a[2005];
    for (int i=0;i<n;++i) scanf("%31s %lf", a[i].name, &a[i].price);
    for (int i=0;i<n-1;++i)
        for (int j=0;j<n-1-i;++j)
            if (cmp(a[j],a[j+1])>0){ Product t=a[j]; a[j]=a[j+1]; a[j+1]=t; }
    for (int i=0;i<n;++i) printf("%s %.2f%s", a[i].name, a[i].price, (i<n-1)?"\n":"");
    return 0;
}
```

---

### 8) Sensor Packet View (Union: Int vs. Bytes) — **Hard**

**Problem:**
An embedded sensor transmits a 32-bit status as raw bytes. A union lets tools read the same memory as an integer or as four bytes. Read four byte values into the union’s `b[0..3]` **in memory order**, print the combined unsigned integer, then echo the bytes back.

**Input Format:**
`b0 b1 b2 b3` (each 0–255)

**Output Format:**
Line 1: `<u>`
Line 2: `<b0> <b1> <b2> <b3>`

**Test Cases:**

1. **Explanation:** Writing bytes and reading `u` reflects memory view; echo proves storage.
   **Input:**

```
1 0 0 0
```

**Output:**

```
1
1 0 0 0
```

2. **Explanation:** All zero reconstructs to zero.
   **Input:**

```
0 0 0 0
```

**Output:**

```
0
0 0 0 0
```

3.

**Input:**

```
255 255 255 255
```

**Output:**

```
4294967295
255 255 255 255
```

4.

**Input:**

```
2 1 0 0
```

**Output:**

```
258
2 1 0 0
```

5.

**Input:**

```
10 20 30 40
```

**Output:**

```
673059850
10 20 30 40
```

6.

**Input:**

```
170 187 204 221
```

**Output:**

```
3721182122
170 187 204 221
```

7.

**Input:**

```
16 0 1 0
```

**Output:**

```
65552
16 0 1 0
```

**Solution (C):**

```c
#include <stdio.h>

union Packet { unsigned int u; unsigned char b[4]; };

int main(void){
    union Packet p;
    unsigned int x0,x1,x2,x3;
    if (scanf("%u %u %u %u",&x0,&x1,&x2,&x3)!=4) return 0;
    p.b[0]=(unsigned char)x0; p.b[1]=(unsigned char)x1;
    p.b[2]=(unsigned char)x2; p.b[3]=(unsigned char)x3;
    printf("%u\n", p.u);
    printf("%u %u %u %u", (unsigned)p.b[0], (unsigned)p.b[1], (unsigned)p.b[2], (unsigned)p.b[3]);
    return 0;
}
```

---

### 9) Temperature Record (Union of Scales) — **Hard**

**Problem:**
A logger stores a reading either as Celsius or Fahrenheit. Downstream analytics need Celsius. Use `union { double c; double f; }` inside `struct { char scale; Temp t; }`. Read one record, convert to Celsius if needed, and print to two decimals.

**Input Format:**
`scale value` (scale is `C` or `F`)

**Output Format:**
Celsius value to two decimals

**Test Cases:**

1. **Explanation:** Already Celsius.
   **Input:**

```
C 25
```

**Output:**

```
25.00
```

2. **Explanation:** Boiling point conversion.
   **Input:**

```
F 212
```

**Output:**

```
100.00
```

3.

**Input:**

```
F 32
```

**Output:**

```
0.00
```

4.

**Input:**

```
C -40
```

**Output:**

```
-40.00
```

5.

**Input:**

```
F 98.6
```

**Output:**

```
37.00
```

6.

**Input:**

```
C 0
```

**Output:**

```
0.00
```

7.

**Input:**

```
F 451
```

**Output:**

```
232.78
```

**Solution (C):**

```c
#include <stdio.h>

typedef union { double c; double f; } Temp;
typedef struct { char scale; Temp t; } Rec;

double toC(Rec r){
    if (r.scale=='C' || r.scale=='c') return r.t.c;
    return (r.t.f - 32.0) * 5.0/9.0;
}

int main(void){
    Rec r; if (scanf(" %c %lf",&r.scale, &r.t.c)!=2) return 0; // reuse member space
    printf("%.2f", toC(r));
    return 0;
}
```

---

### 10) RGB Mixer (Union Overlay with Byte Struct) — **Hard**

**Problem:**
A graphics pipeline packs RGBA channels into a 32-bit field. Debugging often requires both the packed integer and individual channels. Use `typedef struct { unsigned char r,g,b,a; } RGBA;` and `typedef union { RGBA ch; unsigned int packed; } Color;`. Read `r g b a`, fill `ch`, print `packed`, then print `r g b a` to verify overlay.

**Input Format:**
`r g b a` (0–255 each)

**Output Format:**
Line 1: `<packed_uint>`
Line 2: `<r> <g> <b> <a>`

**Test Cases:**

1. **Explanation:** Red with full alpha.
   **Input:**

```
255 0 0 255
```

**Output:**

```
4294902015
255 0 0 255
```

2. **Explanation:** Overlay visible; bytes echoed.
   **Input:**

```
0 255 0 128
```

**Output:**

```
2164195456
0 255 0 128
```

3.

**Input:**

```
0 0 255 0
```

**Output:**

```
16711680
0 0 255 0
```

4.

**Input:**

```
10 20 30 40
```

**Output:**

```
675010570
10 20 30 40
```

5.

**Input:**

```
1 2 3 4
```

**Output:**

```
67305985
1 2 3 4
```

6.

**Input:**

```
170 187 204 221
```

**Output:**

```
3721182122
170 187 204 221
```

7.

**Input:**

```
16 32 48 64
```

**Output:**

```
1077952576
16 32 48 64
```

**Solution (C):**

```c
#include <stdio.h>

typedef struct { unsigned char r,g,b,a; } RGBA;
typedef union  { RGBA ch; unsigned int packed; } Color;

int main(void){
    unsigned int R,G,B,A; if (scanf("%u %u %u %u",&R,&G,&B,&A)!=4) return 0;
    Color c; c.ch.r=(unsigned char)R; c.ch.g=(unsigned char)G; c.ch.b=(unsigned char)B; c.ch.a=(unsigned char)A;
    printf("%u\n", c.packed);
    printf("%u %u %u %u", (unsigned)c.ch.r, (unsigned)c.ch.g, (unsigned)c.ch.b, (unsigned)c.ch.a);
    return 0;
}
```

