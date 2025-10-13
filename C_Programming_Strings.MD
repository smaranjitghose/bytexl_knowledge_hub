

## **1. Social Post Validator**

Your university’s new social networking platform, *BuzzBoard*, limits every post to 140 characters. Users often type long messages, and before their post is accepted, the system must check its length and suggest trimming if it’s too long. Write a program that reads a post (which may include spaces), counts the number of characters using `strlen()`, and prints `"OK"` if it fits the limit or `"TRIM n"` if it exceeds it, where `n` is the number of extra characters.

### **Input Format**

* A single line containing a string (may include spaces).

### **Output Format**

* Print `"OK"` if the post length ≤ 140.
* Otherwise print `"TRIM n"` where `n` = number of characters over the limit.

### **Test Cases**

1.

Input: `Hello World!`
Output: `OK`

2.

Input: `This is a test post with exactly 140 characters..............................................................................................................`
Output: `OK`

3.

Input: `This post goes beyond the limit because it keeps going and going and going until it surely crosses one hundred and forty characters.`
Output: `TRIM 16`

4.

Input: (Empty line)
Output: `OK`

5.

Input: `A very short post.`
Output: `OK`

6.

Input: `1234567890` repeated 14 times (140 characters exactly)
Output: `OK`

7.

Input: `1234567890` repeated 15 times (150 characters)
Output: `TRIM 10`

---

### **Solution**


```c
#include <stdio.h>
#include <string.h>

int main(void) {
    char s[2005];
    if (!fgets(s, sizeof(s), stdin)) return 0;
    size_t len = strlen(s);
    if (len > 0 && s[len - 1] == '\n') { s[--len] = '\0'; }
    if (len <= 140) {
        printf("OK");
    } else {
        printf("TRIM %lu", (unsigned long)(len - 140));
    }
    return 0;
}

```




## **2. Profile Name Mirror**

The college portal stores a user’s display name securely before updating it across systems. To ensure correctness, the system needs to display a read-only mirror of whatever name the user has entered. Write a program that reads a user’s name, copies it into another string using `strcpy()`, and prints the mirrored copy so users can confirm their identity before submission.

### **Input Format**

* A single line containing the user’s display name.

### **Output Format**

* Print the copied string.

### **Test Cases**

1.

Input: `byteXL Learner`
Output: `byteXL Learner`

2.

Input: `Amit`
Output: `Amit`

3.

Input: `Rohan Sharma`
Output: `Rohan Sharma`

4.

Input: (Empty line)
Output: (Empty line)

5.

Input: `name_with_underscores`
Output: `name_with_underscores`

6.

Input: `12345`
Output: `12345`

7.

Input: `ThisNameIsExactlyHundredCharactersLong..............................................................................`
Output: Same string

---


### **Solution**

```c
#include <stdio.h>
#include <string.h>

int main(void) {
    char name[102], mirror[102];
    if (!fgets(name, sizeof(name), stdin)) return 0;
    size_t len = strlen(name);
    if (len > 0 && name[len - 1] == '\n') name[len - 1] = '\0';
    strcpy(mirror, name);
    printf("%s", mirror);
    return 0;
}
```


## **3. Case-Insensitive Username Filter**

In the signup module of your portal, duplicate usernames must be avoided regardless of case. For instance, “Riya” and “riya” should be considered the same user. Write a program that takes two usernames and compares them manually, character by character, ignoring case differences. If the two usernames are identical ignoring case, print `"DUPLICATE"`, otherwise print `"UNIQUE"`.

### **Input Format**

* Two lines:

  * Line 1: First username
  * Line 2: Second username

### **Output Format**

* Print `"DUPLICATE"` or `"UNIQUE"`

### **Test Cases**

1.

Input:

```
Riya
riya
```

Output: `DUPLICATE`

2.

Input:

```
Aman
Aman
```

Output: `DUPLICATE`

3.

Input:

```
John
Johnny
```

Output: `UNIQUE`

4.

Input:

```
HELLO
hello
```

Output: `DUPLICATE`

5.

Input:

```
CSStudent
CsStudent
```

Output: `DUPLICATE`

6.

Input:

```
alex
ALExa
```

Output: `UNIQUE`

7.

Input:

```
Code
code123
```

Output: `UNIQUE`

### **Solution**

```c
#include <stdio.h>
#include <string.h>

static char tolow(char c) {
    if (c >= 'A' && c <= 'Z') return c + ('a' - 'A');
    return c;
}

int main(void) {
    char a[205], b[205];
    if (!fgets(a, sizeof(a), stdin)) return 0;
    if (!fgets(b, sizeof(b), stdin)) return 0;
    size_t la = strlen(a), lb = strlen(b);
    if (la > 0 && a[la - 1] == '\n') a[--la] = '\0';
    if (lb > 0 && b[lb - 1] == '\n') b[--lb] = '\0';

    if (la != lb) { printf("UNIQUE"); return 0; }

    int same = 1;
    for (size_t i = 0; i < la; i++) {
        if (tolow(a[i]) != tolow(b[i])) { same = 0; break; }
    }
    printf("%s", same ? "DUPLICATE" : "UNIQUE");
    return 0;
}

```

## **4. File Path Builder**

The IT support team frequently stores student data in separate directories on the server. When generating reports, they often need to combine a directory path and a filename into a complete file path. Write a program that reads a directory and a filename and joins them using `strcat()`, making sure there is exactly one `/` between them.

### **Input Format**

* Two lines:

  * Line 1: Directory path
  * Line 2: Filename

### **Output Format**

* Print the combined path.

### **Test Cases**

1.

Input:

```
/home/student
notes.txt
```

Output: `/home/student/notes.txt`

2.

Input:

```
/home/student/
/data.csv
```

Output: `/home/student//data.csv`

3.

Input:

```
/usr/local
log.txt
```

Output: `/usr/local/log.txt`

4.

Input:

```
/
config.yaml
```

Output: `//config.yaml`

5.

Input:

```
docs
report.docx
```

Output: `docs/report.docx`

6.

Input:

```
D:
file.c
```

Output: `D:/file.c`

7.

Input:

```
/tmp
```

Output: `/tmp/`

---

### **Solution**

```c
#include <stdio.h>
#include <string.h>

int main(void) {
    char dir[205], file[205], path[410];
    if (!fgets(dir, sizeof(dir), stdin)) return 0;
    if (!fgets(file, sizeof(file), stdin)) return 0;

    size_t ld = strlen(dir), lf = strlen(file);
    if (ld > 0 && dir[ld - 1] == '\n') dir[--ld] = '\0';
    if (lf > 0 && file[lf - 1] == '\n') file[--lf] = '\0';

    path[0] = '\0';
    strcat(path, dir);
    if (ld == 0 || dir[ld - 1] != '/') strcat(path, "/");
    strcat(path, file);

    printf("%s", path);
    return 0;
}
```



## **5. Secure Log Redactor**

Your system’s log files often include confidential information, with secrets appearing after a `#` symbol on each line. For security, everything after the first `#` should be removed before logs are exported.

### **Input Format**

* A single line containing a log entry.

### **Output Format**

* Print the redacted string, removing everything after `#`.

### **Test Cases**

1.

Input: `TOKEN=abc#donotshare`
Output: `TOKEN=abc`

2.

Input: `API_KEY=xyz123`
Output: `API_KEY=xyz123`

3.

Input: `password#hiddenvalue`
Output: `password`

4.

Input: `#topsecret`
Output: (Empty line)

5.

Input: `visible#then#hidden`
Output: `visible`

6.

Input: `HelloWorld`
Output: `HelloWorld`

7.

Input: (Empty line)
Output: (Empty line)


```c
#include <stdio.h>
#include <string.h>

int main(void) {
    char src[2005], dst[2005];
    if (!fgets(src, sizeof(src), stdin)) return 0;
    size_t ls = strlen(src);
    if (ls > 0 && src[ls - 1] == '\n') src[--ls] = '\0';

    size_t i = 0, j = 0;
    while (src[i] != '\0' && src[i] != '#') {
        dst[j++] = src[i++];
    }
    dst[j] = '\0';
    printf("%s", dst);
    return 0;
}
```



## **6. Ticket Code Decoder**

The annual tech fest encodes event tickets by reversing the seat IDs. For example, a seat labeled “A12” is stored as “21A”. You must decode the ticket ID before printing it.

### **Input Format**

* A single line containing the reversed seat ID.

### **Output Format**

* Print the decoded seat ID.

### **Test Cases**

1.

Input: `21A`
Output: `A12`

2.

Input: `543ZY`
Output: `YZ345`

3.

Input: `A`
Output: `A`

4.

Input: `9B`
Output: `B9`

5.

Input: `C0`
Output: `0C`

6.

Input: `AAA`
Output: `AAA`

7.

Input: (Empty line)
Output: (Empty line)


```c
#include <stdio.h>
#include <string.h>

int main(void) {
    char s[205];
    if (!fgets(s, sizeof(s), stdin)) return 0;
    size_t n = strlen(s);
    if (n > 0 && s[n - 1] == '\n') s[--n] = '\0';

    if (n > 1) {
        size_t i = 0, j = n - 1;
        while (i < j) {
            char t = s[i]; s[i] = s[j]; s[j] = t;
            i++; j--;
        }
    }
    printf("%s", s);
    return 0;
}
```

## **7. Smart Product Label Generator**

In your college’s innovation lab, student teams print product labels by combining their brand and model names. To make the label neat, if the brand name ends with the same character that the model name starts with, that character should not be duplicated.

### **Input Format**

* Two lines:

  * Line 1: Brand name
  * Line 2: Model name

### **Output Format**

* Print the combined label.

### **Test Cases**

1.

Input:

```
Max
Xtreme
```

Output: `Maxtreme`

2.

Input:

```
Nano
Optic
```

Output: `NanoOptic`

3.

Input:

```
alpha
alpha
```

Output: `alphaalpha`

4.

Input:

```
Light
tastic
```

Output: `Lightastic`

5.

Input:

```
Zeno
Omega
```

Output: `ZenoOmega`

6.

Input:

```
Fast
Speed
```

Output: `FastSpeed`

7.

Input:

```
Power
Ranger
```

Output: `PowerRanger`

```c
#include <stdio.h>
#include <string.h>

static char tolow(char c){ return (c >= 'A' && c <= 'Z') ? (c + 'a' - 'A') : c; }

int main(void) {
    char brand[205], model[205], label[410];
    if (!fgets(brand, sizeof(brand), stdin)) return 0;
    if (!fgets(model, sizeof(model), stdin)) return 0;

    size_t lb = strlen(brand), lm = strlen(model);
    if (lb > 0 && brand[lb - 1] == '\n') brand[--lb] = '\0';
    if (lm > 0 && model[lm - 1] == '\n') model[--lm] = '\0';

    // copy brand
    size_t i = 0, k = 0;
    for (; i < lb; i++) label[k++] = brand[i];

    // decide starting index for model
    size_t start = 0;
    if (lb > 0 && lm > 0) {
        char lastb = tolow(brand[lb - 1]);
        char firstm = tolow(model[0]);
        if (lastb == firstm) start = 1; // avoid duplication
    }

    for (size_t j = start; j < lm; j++) label[k++] = model[j];
    label[k] = '\0';

    printf("%s", label);
    return 0;
}

```

## **8. Keyword Suggestion Engine**

Your academic portal suggests topics as users type. When a query exactly matches a stored keyword, the system confirms it. Otherwise, it suggests users keep typing.

### **Input Format**

* Two lines:

  * Line 1: Query string
  * Line 2: Keyword string

### **Output Format**

* Print `"Exact match"` if identical, else `"Keep typing"`.

### **Test Cases**

1.

Input:

```
pointers
pointers
```

Output: `Exact match`

2.

Input:

```
Array
array
```

Output: `Keep typing`

3.

Input:

```
C
C
```

Output: `Exact match`

4.

Input:

```
program
programs
```

Output: `Keep typing`

5.

Input:

```
OS
OS
```

Output: `Exact match`

6.

Input:

```
Java
JavaScript
```

Output: `Keep typing`

7.

Input:

```
Loops
loops
```
Output: `Keep typing`

```c
#include <stdio.h>
#include <string.h>

int main(void) {
    char query[205], keyword[205];
    if (!fgets(query, sizeof(query), stdin)) return 0;
    if (!fgets(keyword, sizeof(keyword), stdin)) return 0;

    size_t lq = strlen(query), lk = strlen(keyword);
    if (lq > 0 && query[lq - 1] == '\n') query[--lq] = '\0';
    if (lk > 0 && keyword[lk - 1] == '\n') keyword[--lk] = '\0';

    printf("%s", strcmp(query, keyword) == 0 ? "Exact match" : "Keep typing");
    return 0;
}
```

## **9. Readability Analyzer**

A writing assistant tool for CS students measures readability by calculating the proportion of vowels to total letters. Write a program that counts vowels (`a, e, i, o, u` in any case) and letters, and prints the ratio as `vowels/letters`.

### **Input Format**

* A single line of text.

### **Output Format**

* Print `X/Y` where `X` is the number of vowels and `Y` is the number of letters.

### **Test Cases**

1.

Input: `C is close to metal.`
Output: `6/14`

2.

Input: `Hello`
Output: `2/5`

3.

Input: `AEIOU`
Output: `5/5`

4.

Input: `xyz`
Output: `0/3`

5.

Input: `12345`
Output: `0/0`

6.

Input: (Empty line)
Output: `0/0`

7.

Input: `Education is key!`
Output: `7/13`

```c
#include <stdio.h>
#include <string.h>

static int is_letter(char c) {
    return (c >= 'A' && c <= 'Z') || (c >= 'a' && c <= 'z');
}
static int is_vowel(char c) {
    if (c >= 'A' && c <= 'Z') c = c + ('a' - 'A');
    return c=='a'||c=='e'||c=='i'||c=='o'||c=='u';
}

int main(void) {
    char s[2005];
    if (!fgets(s, sizeof(s), stdin)) return 0;

    size_t len = strlen(s);
    if (len > 0 && s[len - 1] == '\n') s[--len] = '\0';

    int letters = 0, vowels = 0;
    for (size_t i = 0; i < len; i++) {
        if (is_letter(s[i])) {
            letters++;
            if (is_vowel(s[i])) vowels++;
        }
    }
    printf("%d/%d", vowels, letters);
    return 0;
}

```

## **10. Palindromic License Detector**

The robotics club maintains robot license plates and highlights those that are palindromes — strings that read the same forward and backward. Plates may contain dashes or spaces, which should be ignored, and comparison should be case-insensitive.

### **Input Format**

* A single line containing a license plate string.

### **Output Format**

* Print `"PALINDROME"` if the plate reads the same both ways (ignoring spaces, dashes, and case), otherwise `"NOT PALINDROME"`.

### **Test Cases**

1.

Input: `AB-cc-BA`
Output: `PALINDROME`

2.

Input: `Race car`
Output: `PALINDROME`

3.

Input: `XYx`
Output: `PALINDROME`

4.

Input: `abc`
Output: `NOT PALINDROME`

5.

Input: `A man a plan a canal Panama`
Output: `PALINDROME`

6.

Input: `Level`
Output: `PALINDROME`

7.

Input: `ByteXL`
Output: `NOT PALINDROME`


```c
#include <stdio.h>
#include <string.h>

static int is_alnum_ascii(char c) {
    if (c >= '0' && c <= '9') return 1;
    if (c >= 'A' && c <= 'Z') return 1;
    if (c >= 'a' && c <= 'z') return 1;
    return 0;
}
static char tolow(char c) {
    if (c >= 'A' && c <= 'Z') return c + ('a' - 'A');
    return c;
}

int main(void) {
    char in[2005], norm[2005];
    if (!fgets(in, sizeof(in), stdin)) return 0;
    size_t n = strlen(in);
    if (n > 0 && in[n - 1] == '\n') in[--n] = '\0';

    size_t k = 0;
    for (size_t i = 0; i < n; i++) {
        if (is_alnum_ascii(in[i])) norm[k++] = tolow(in[i]);
    }
    norm[k] = '\0';

    int ispal = 1;
    if (k > 1) {
        size_t i = 0, j = k - 1;
        while (i < j) {
            if (norm[i] != norm[j]) { ispal = 0; break; }
            i++; j--;
        }
    }
    printf("%s", ispal ? "PALINDROME" : "NOT PALINDROME");
    return 0;
}


```

