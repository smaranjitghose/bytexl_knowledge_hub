### **1. Medical Record Swapper**   

In a busy hospital triage system, two patient IDs were accidentally logged in reverse order due to a keyboard misinput; to correct this without extra memory, you must write a C program that reads two patient IDs and swaps their values directly in memory using pointers.

**Input Format:**  
- One line with two space-separated integers: `id1 id2`  

**Output Format:**  
```
Before correction: Patient A = X, Patient B = Y  
After correction: Patient A = Y, Patient B = X
```

---

### **2. Voice Assistant Vowel Analyzer**  

To improve speech recognition accuracy in a smart home voice assistant, you need to analyze user commands by counting vowels (a, e, i, o, u—case-insensitive) using efficient pointer-based string traversal instead of library functions.

**Input Format:**  
- One line: a single spoken word (no spaces)  

**Output Format:**  
```
Vowel count in command: X
```
---

### **3. Warehouse Inventory Sorter**  

A logistics robot in a smart warehouse must sort incoming product IDs in ascending order for shelf placement, and to conserve memory on its embedded controller, you’ll implement an in-place sorting algorithm using only pointer arithmetic.

**Input Format:**  
- First line: `n` (number of products)  
- Second line: `n` space-separated integers (product IDs)  

**Output Format:**  
```
Sorted inventory: X1 X2 ... Xn
```
---

### **4. Flight Data Reverser**  

An aviation diagnostics tool needs to simulate ascent profiles by reversing a sequence of recorded descent altitudes; to do this efficiently on an aircraft’s onboard computer, you’ll reverse the altitude array using pointer-based swapping from both ends.

**Input Format:**  
- First line: `n` (number of altitude readings)  
- Next `n` lines: one integer per line (altitude in feet)  

**Output Format:**  
```
Original descent log: A1 A2 ... An  
Reversed (ascent simulation): An ... A2 A1
```

---

### **5. Sensor Data Comparator**  

In a climate-controlled laboratory, two temperature sensors report real-time readings, and a safety module must instantly identify the higher value using pointer dereferencing to decide whether to activate the emergency cooling system.

**Input Format:**  
- One line: two space-separated floats `temp1 temp2`  

**Output Format:**  
```
Critical temperature detected: X.XX°C
```

---

### **6. Password Length Validator**  

On a legacy security terminal with no standard string libraries, you must validate user password length during registration by manually traversing the input string with pointers to count characters for policy compliance.

**Input Format:**  
- One line: password string (no spaces)  

**Output Format:**  
```
Password length: X characters
```

---

### **7. Smart Home Energy Aggregator**  

A microcontroller in a smart home system collects hourly energy usage (in kWh) from sensors and must compute the total daily consumption using pointer arithmetic to minimize CPU cycles and extend battery life.

**Input Format:**  
- First line: `n` (number of hours)  
- Second line: `n` space-separated floats  

**Output Format:**  
```
Total energy consumed: X.XX kWh
```

---

### **8. Customer Feedback Emphasis Detector**  

A restaurant’s automated feedback analyzer scans online reviews for emotional emphasis by counting occurrences of a specific character (like '!') using pointer-based string scanning to gauge customer excitement without regex or libraries.

**Input Format:**  
- First line: review string (no spaces)  
- Second line: character to count  

**Output Format:**  
```
Emphasis markers ('X'): Y
```

---

### **9. Agricultural Yield Monitor**  

A drone monitoring crop health across multiple fields records yield estimates per plot, and to quickly flag underperforming zones on its resource-limited processor, it must find the minimum yield using pointer traversal through the data array.

**Input Format:**  
- First line: `n` (number of plots)  
- Second line: `n` space-separated floats (yield in kg)  

**Output Format:**  
```
Lowest yield detected: X.XX kg
```

---

### **10. IoT Firmware Command Duplicator**  

An IoT device with strict firmware size limits receives a configuration command and must create a backup copy in a separate memory buffer using raw pointer operations—without any standard string functions—to ensure safe recovery after reboots.

**Input Format:**  
- One line: command string (no spaces)  

**Output Format:**  
```
Original command: SOURCE  
Backup buffer: SOURCE
```

---

### **1. Medical Record Swapper**

**C Solution:**
```c
#include <stdio.h>

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int a, b;
    scanf("%d %d", &a, &b);
    printf("Before correction: Patient A = %d, Patient B = %d\n", a, b);
    swap(&a, &b);
    printf("After correction: Patient A = %d, Patient B = %d\n", a, b);
    return 0;
}
```

**Test Cases:**  
1. Input: `10 20` → Output: `Before correction: Patient A = 10, Patient B = 20` → `After correction: Patient A = 20, Patient B = 10`  
2. Input: `0 0` → Output: `Before correction: Patient A = 0, Patient B = 0` → `After correction: Patient A = 0, Patient B = 0`  
3. Input: `-5 10` → Output: `Before correction: Patient A = -5, Patient B = 10` → `After correction: Patient A = 10, Patient B = -5`  
4. Input: `100 1` → Output: `Before correction: Patient A = 100, Patient B = 1` → `After correction: Patient A = 1, Patient B = 100`  
5. Input: `999 999` → Output: `Before correction: Patient A = 999, Patient B = 999` → `After correction: Patient A = 999, Patient B = 999`  
6. Input: `1 -1` → Output: `Before correction: Patient A = 1, Patient B = -1` → `After correction: Patient A = -1, Patient B = 1`  
7. Input: `5000 2500` → Output: `Before correction: Patient A = 5000, Patient B = 2500` → `After correction: Patient A = 2500, Patient B = 5000`

---

### **2. Voice Assistant Vowel Analyzer**

**C Solution:**
```c
#include <stdio.h>

int isVowel(char c) {
    if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u' ||
        c == 'A' || c == 'E' || c == 'I' || c == 'O' || c == 'U')
        return 1;
    return 0;
}

int main() {
    char word[100];
    scanf("%s", word);
    char *ptr = word;
    int count = 0;
    while (*ptr != '\0') {
        if (isVowel(*ptr)) count++;
        ptr++;
    }
    printf("Vowel count in command: %d\n", count);
    return 0;
}
```

**Test Cases:**  
1. Input: `hello` → Output: `Vowel count in command: 2`  
2. Input: `bcdfg` → Output: `Vowel count in command: 0`  
3. Input: `AEIOU` → Output: `Vowel count in command: 5`  
4. Input: `Programming` → Output: `Vowel count in command: 3`  
5. Input: `a` → Output: `Vowel count in command: 1`  
6. Input: `Sky` → Output: `Vowel count in command: 0`  
7. Input: `Education` → Output: `Vowel count in command: 5`

---

### **3. Warehouse Inventory Sorter**

**C Solution:**
```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);
    int arr[100];
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    // Bubble sort using pointers
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            int *p1 = &arr[j];
            int *p2 = &arr[j + 1];
            if (*p1 > *p2) {
                int temp = *p1;
                *p1 = *p2;
                *p2 = temp;
            }
        }
    }
    
    printf("Sorted inventory:");
    for (int i = 0; i < n; i++) {
        printf(" %d", arr[i]);
    }
    printf("\n");
    return 0;
}
```

**Test Cases:**  
1. Input: `5` `3 1 4 1 5` → Output: `Sorted inventory: 1 1 3 4 5`  
2. Input: `1` `42` → Output: `Sorted inventory: 42`  
3. Input: `3` `9 5 2` → Output: `Sorted inventory: 2 5 9`  
4. Input: `4` `10 10 10 10` → Output: `Sorted inventory: 10 10 10 10`  
5. Input: `6` `6 5 4 3 2 1` → Output: `Sorted inventory: 1 2 3 4 5 6`  
6. Input: `2` `-1 5` → Output: `Sorted inventory: -1 5`  
7. Input: `0` → Output: `Sorted inventory:`

---

### **4. Flight Data Reverser**

**C Solution:**
```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);
    int arr[100];
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("Original descent log:");
    for (int i = 0; i < n; i++) {
        printf(" %d", arr[i]);
    }
    printf("\n");
    
    // Reverse using pointers
    int *start = arr;
    int *end = arr + n - 1;
    while (start < end) {
        int temp = *start;
        *start = *end;
        *end = temp;
        start++;
        end--;
    }
    
    printf("Reversed (ascent simulation):");
    for (int i = 0; i < n; i++) {
        printf(" %d", arr[i]);
    }
    printf("\n");
    return 0;
}
```

**Test Cases:**  
1. Input: `3` `100 200 300` → Output: `Original descent log: 100 200 300` → `Reversed (ascent simulation): 300 200 100`  
2. Input: `1` `500` → Output: `Original descent log: 500` → `Reversed (ascent simulation): 500`  
3. Input: `4` `1 2 3 4` → Output: `Original descent log: 1 2 3 4` → `Reversed (ascent simulation): 4 3 2 1`  
4. Input: `2` `10 20` → Output: `Original descent log: 10 20` → `Reversed (ascent simulation): 20 10`  
5. Input: `5` `5 4 3 2 1` → Output: `Original descent log: 5 4 3 2 1` → `Reversed (ascent simulation): 1 2 3 4 5`  
6. Input: `0` → Output: `Original descent log:` → `Reversed (ascent simulation):`  
7. Input: `3` `-10 0 10` → Output: `Original descent log: -10 0 10` → `Reversed (ascent simulation): 10 0 -10`

---

### **5. Sensor Data Comparator**

**C Solution:**
```c
#include <stdio.h>

int main() {
    float t1, t2;
    scanf("%f %f", &t1, &t2);
    float *p1 = &t1;
    float *p2 = &t2;
    float max = (*p1 > *p2) ? *p1 : *p2;
    printf("Critical temperature detected: %.2f°C\n", max);
    return 0;
}
```

**Test Cases:**  
1. Input: `23.5 27.8` → Output: `Critical temperature detected: 27.80°C`  
2. Input: `0.0 0.0` → Output: `Critical temperature detected: 0.00°C`  
3. Input: `-5.5 3.2` → Output: `Critical temperature detected: 3.20°C`  
4. Input: `100.0 99.9` → Output: `Critical temperature detected: 100.00°C`  
5. Input: `15.75 15.75` → Output: `Critical temperature detected: 15.75°C`  
6. Input: `-10.0 -20.0` → Output: `Critical temperature detected: -10.00°C`  
7. Input: `0.1 0.01` → Output: `Critical temperature detected: 0.10°C`

---

### **6. Password Length Validator**

**C Solution:**
```c
#include <stdio.h>

int main() {
    char password[100];
    scanf("%s", password);
    char *ptr = password;
    int len = 0;
    while (*ptr != '\0') {
        len++;
        ptr++;
    }
    printf("Password length: %d characters\n", len);
    return 0;
}
```

**Test Cases:**  
1. Input: `hello` → Output: `Password length: 5 characters`  
2. Input: `a` → Output: `Password length: 1 characters`  
3. Input: `Secure123` → Output: `Password length: 9 characters`  
4. Input: `x` → Output: `Password length: 1 characters`  
5. Input: `ABCDEFGHIJKLMNOP` → Output: `Password length: 16 characters`  
6. Input: `1234567890` → Output: `Password length: 10 characters`  
7. Input: `!@#$%` → Output: `Password length: 5 characters`

---

### **7. Smart Home Energy Aggregator**

**C Solution:**
```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);
    float readings[100];
    for (int i = 0; i < n; i++) {
        scanf("%f", &readings[i]);
    }
    
    float *ptr = readings;
    float total = 0.0;
    for (int i = 0; i < n; i++) {
        total += *ptr;
        ptr++;
    }
    
    printf("Total energy consumed: %.2f kWh\n", total);
    return 0;
}
```

**Test Cases:**  
1. Input: `4` `1.2 0.8 1.5 0.9` → Output: `Total energy consumed: 4.40 kWh`  
2. Input: `1` `5.0` → Output: `Total energy consumed: 5.00 kWh`  
3. Input: `3` `0.0 0.0 0.0` → Output: `Total energy consumed: 0.00 kWh`  
4. Input: `2` `2.5 2.5` → Output: `Total energy consumed: 5.00 kWh`  
5. Input: `5` `1.1 2.2 3.3 4.4 5.5` → Output: `Total energy consumed: 16.50 kWh`  
6. Input: `0` → Output: `Total energy consumed: 0.00 kWh`  
7. Input: `3` `10.0 0.1 0.01` → Output: `Total energy consumed: 10.11 kWh`

---

### **8. Customer Feedback Emphasis Detector**

**C Solution:**
```c
#include <stdio.h>

int main() {
    char review[100];
    char target;
    scanf("%s", review);
    scanf(" %c", &target);
    
    char *ptr = review;
    int count = 0;
    while (*ptr != '\0') {
        if (*ptr == target) count++;
        ptr++;
    }
    
    printf("Emphasis markers ('%c'): %d\n", target, count);
    return 0;
}
```

**Test Cases:**  
1. Input: `GreatFood!!!` `!` → Output: `Emphasis markers ('!'): 3`  
2. Input: `Hello` `l` → Output: `Emphasis markers ('l'): 2`  
3. Input: `aaaa` `a` → Output: `Emphasis markers ('a'): 4`  
4. Input: `Test` `z` → Output: `Emphasis markers ('z'): 0`  
5. Input: `A` `A` → Output: `Emphasis markers ('A'): 1`  
6. Input: `Programming` `m` → Output: `Emphasis markers ('m'): 2`  
7. Input: `12321` `2` → Output: `Emphasis markers ('2'): 2`

---

### **9. Agricultural Yield Monitor**

**C Solution:**
```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);
    float yields[100];
    for (int i = 0; i < n; i++) {
        scanf("%f", &yields[i]);
    }
    
    if (n == 0) {
        printf("Lowest yield detected: 0.00 kg\n");
        return 0;
    }
    
    float *ptr = yields;
    float min = *ptr;
    for (int i = 1; i < n; i++) {
        ptr++;
        if (*ptr < min) min = *ptr;
    }
    
    printf("Lowest yield detected: %.2f kg\n", min);
    return 0;
}
```

**Test Cases:**  
1. Input: `5` `120.5 98.2 105.0 87.3 110.8` → Output: `Lowest yield detected: 87.30 kg`  
2. Input: `1` `50.0` → Output: `Lowest yield detected: 50.00 kg`  
3. Input: `3` `10.0 5.5 7.2` → Output: `Lowest yield detected: 5.50 kg`  
4. Input: `4` `100.0 100.0 100.0 100.0` → Output: `Lowest yield detected: 100.00 kg`  
5. Input: `2` `-10.0 5.0` → Output: `Lowest yield detected: -10.00 kg`  
6. Input: `0` → Output: `Lowest yield detected: 0.00 kg`  
7. Input: `3` `0.1 0.01 0.001` → Output: `Lowest yield detected: 0.00 kg` (rounded to 2 decimals → 0.00)

> **Note:** For test case 7, `0.001` prints as `0.00` due to `%.2f`.

---

### **10. IoT Firmware Command Duplicator**

**C Solution:**
```c
#include <stdio.h>

int main() {
    char source[100], dest[100];
    scanf("%s", source);
    
    char *src = source;
    char *dst = dest;
    while (*src != '\0') {
        *dst = *src;
        src++;
        dst++;
    }
    *dst = '\0';
    
    printf("Original command: %s\n", source);
    printf("Backup buffer: %s\n", dest);
    return 0;
}
```

**Test Cases:**  
1. Input: `REBOOT` → Output: `Original command: REBOOT` → `Backup buffer: REBOOT`  
2. Input: `a` → Output: `Original command: a` → `Backup buffer: a`  
3. Input: `12345` → Output: `Original command: 12345` → `Backup buffer: 12345`  
4. Input: `CMD` → Output: `Original command: CMD` → `Backup buffer: CMD`  
5. Input: `X` → Output: `Original command: X` → `Backup buffer: X`  
6. Input: `ShutdownNow` → Output: `Original command: ShutdownNow` → `Backup buffer: ShutdownNow`  
7. Input: `!@#` → Output: `Original command: !@#` → `Backup buffer: !@#`

---

All solutions use only `int`, `float`, `char`, arrays, and pointers as requested. Each includes exactly 7 test cases covering edge cases like empty input, negatives, duplicates, and single elements.
