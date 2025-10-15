### **1. Medical Record Swapper**  
**Max Score:** 5 | **Difficulty:** Easy  

In a busy hospital triage system, two patient IDs were accidentally logged in reverse order due to a keyboard misinput; to correct this without extra memory, you must write a C program that reads two patient IDs and swaps their values directly in memory using pointers.

**Input Format:**  
- One line with two space-separated integers: `id1 id2`  

**Output Format:**  
```
Before correction: Patient A = X, Patient B = Y  
After correction: Patient A = Y, Patient B = X
```

**Sample Input:**  
```
1045 2089
```

**Sample Output:**  
```
Before correction: Patient A = 1045, Patient B = 2089  
After correction: Patient A = 2089, Patient B = 1045
```

---

### **2. Voice Assistant Vowel Analyzer**  
**Max Score:** 5 | **Difficulty:** Easy  

To improve speech recognition accuracy in a smart home voice assistant, you need to analyze user commands by counting vowels (a, e, i, o, u—case-insensitive) using efficient pointer-based string traversal instead of library functions.

**Input Format:**  
- One line: a single spoken word (no spaces)  

**Output Format:**  
```
Vowel count in command: X
```

**Sample Input:**  
```
Activate
```

**Sample Output:**  
```
Vowel count in command: 4
```

---

### **3. Warehouse Inventory Sorter**  
**Max Score:** 5 | **Difficulty:** Easy  

A logistics robot in a smart warehouse must sort incoming product IDs in ascending order for shelf placement, and to conserve memory on its embedded controller, you’ll implement an in-place sorting algorithm using only pointer arithmetic.

**Input Format:**  
- First line: `n` (number of products)  
- Second line: `n` space-separated integers (product IDs)  

**Output Format:**  
```
Sorted inventory: X1 X2 ... Xn
```

**Sample Input:**  
```
5
304 102 506 203 405
```

**Sample Output:**  
```
Sorted inventory: 102 203 304 405 506
```

---

### **4. Flight Data Reverser**  
**Max Score:** 5 | **Difficulty:** Easy  

An aviation diagnostics tool needs to simulate ascent profiles by reversing a sequence of recorded descent altitudes; to do this efficiently on an aircraft’s onboard computer, you’ll reverse the altitude array using pointer-based swapping from both ends.

**Input Format:**  
- First line: `n` (number of altitude readings)  
- Next `n` lines: one integer per line (altitude in feet)  

**Output Format:**  
```
Original descent log: A1 A2 ... An  
Reversed (ascent simulation): An ... A2 A1
```

**Sample Input:**  
```
3
10000
5000
1000
```

**Sample Output:**  
```
Original descent log: 10000 5000 1000  
Reversed (ascent simulation): 1000 5000 10000
```

---

### **5. Sensor Data Comparator**  
**Max Score:** 5 | **Difficulty:** Easy  

In a climate-controlled laboratory, two temperature sensors report real-time readings, and a safety module must instantly identify the higher value using pointer dereferencing to decide whether to activate the emergency cooling system.

**Input Format:**  
- One line: two space-separated floats `temp1 temp2`  

**Output Format:**  
```
Critical temperature detected: X.XX°C
```

**Sample Input:**  
```
23.5 27.8
```

**Sample Output:**  
```
Critical temperature detected: 27.80°C
```

---

### **6. Password Length Validator**  
**Max Score:** 5 | **Difficulty:** Easy  

On a legacy security terminal with no standard string libraries, you must validate user password length during registration by manually traversing the input string with pointers to count characters for policy compliance.

**Input Format:**  
- One line: password string (no spaces)  

**Output Format:**  
```
Password length: X characters
```

**Sample Input:**  
```
SecurePass2024
```

**Sample Output:**  
```
Password length: 14 characters
```

---

### **7. Smart Home Energy Aggregator**  
**Max Score:** 5 | **Difficulty:** Easy  

A microcontroller in a smart home system collects hourly energy usage (in kWh) from sensors and must compute the total daily consumption using pointer arithmetic to minimize CPU cycles and extend battery life.

**Input Format:**  
- First line: `n` (number of hours)  
- Second line: `n` space-separated floats  

**Output Format:**  
```
Total energy consumed: X.XX kWh
```

**Sample Input:**  
```
4
1.2 0.8 1.5 0.9
```

**Sample Output:**  
```
Total energy consumed: 4.40 kWh
```

---

### **8. Customer Feedback Emphasis Detector**  
**Max Score:** 5 | **Difficulty:** Easy  

A restaurant’s automated feedback analyzer scans online reviews for emotional emphasis by counting occurrences of a specific character (like '!') using pointer-based string scanning to gauge customer excitement without regex or libraries.

**Input Format:**  
- First line: review string (no spaces)  
- Second line: character to count  

**Output Format:**  
```
Emphasis markers ('X'): Y
```

**Sample Input:**  
```
GreatFood!!!
!
```

**Sample Output:**  
```
Emphasis markers ('!'): 3
```

---

### **9. Agricultural Yield Monitor**  
**Max Score:** 5 | **Difficulty:** Easy  

A drone monitoring crop health across multiple fields records yield estimates per plot, and to quickly flag underperforming zones on its resource-limited processor, it must find the minimum yield using pointer traversal through the data array.

**Input Format:**  
- First line: `n` (number of plots)  
- Second line: `n` space-separated floats (yield in kg)  

**Output Format:**  
```
Lowest yield detected: X.XX kg
```

**Sample Input:**  
```
5
120.5 98.2 105.0 87.3 110.8
```

**Sample Output:**  
```
Lowest yield detected: 87.30 kg
```

---

### **10. IoT Firmware Command Duplicator**  
**Max Score:** 5 | **Difficulty:** Easy  

An IoT device with strict firmware size limits receives a configuration command and must create a backup copy in a separate memory buffer using raw pointer operations—without any standard string functions—to ensure safe recovery after reboots.

**Input Format:**  
- One line: command string (no spaces)  

**Output Format:**  
```
Original command: SOURCE  
Backup buffer: SOURCE
```

**Sample Input:**  
```
REBOOT_DEVICE
```

**Sample Output:**  
```
Original command: REBOOT_DEVICE  
Backup buffer: REBOOT_DEVICE
```

