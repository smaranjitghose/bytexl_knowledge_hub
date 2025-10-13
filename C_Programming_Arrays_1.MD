## **1. Daily Temperature Tracker**

Your college weather station records the temperature for each day of the week. You need to help the system calculate the **average temperature** from these readings.

### **Input Format**

* First line: an integer `n` (number of days).
* Second line: `n` integers representing daily temperatures.

### **Output Format**

* Print the average temperature rounded down to the nearest integer.

### **Test Cases**

1.

Input:

```
5
30 32 31 29 35
```

Output:

```
31
```

2.

Input:

```
7
25 25 25 25 25 25 25
```

Output:

```
25
```

3.

Input:

```
3
10 20 30
```

Output:

```
20
```

4.

Input:

```
4
0 0 0 0
```

Output:

```
0
```

5.

Input:

```
1
40
```

Output:

```
40
```

6.

Input:

```
6
10 11 12 13 14 15
```

Output:

```
12
```

7.

Input:

```
5
-5 0 5 10 15
```

Output:

```
5
```

---

## **2. Student Score Analyzer**

Your professor keeps a list of marks scored by students in a quiz. You need to find the **highest and lowest marks** from the list.

### **Input Format**

* First line: integer `n` (number of students).
* Second line: `n` integers representing marks.

### **Output Format**

* Print the highest and lowest marks separated by a space.

### **Test Cases**

1.

Input:

```
5
20 50 40 10 30
```

Output:

```
50 10
```

2.

Input:

```
3
100 100 100
```

Output:

```
100 100
```

3.

Input:

```
4
-1 -5 0 3
```

Output:

```
3 -5
```

4.

Input:

```
6
5 4 3 2 1 0
```

Output:

```
5 0
```

5.

Input:

```
1
88
```

Output:

```
88 88
```

6.

Input:

```
8
23 45 67 12 9 78 56 44
```

Output:

```
78 9
```

7.

Input:

```
3
12 11 10
```

Output:

```
12 10
```

---

## **3. Even Number Extractor**

You are given a list of integers from a sensor log. Only the **even numbers** represent valid readings. Print all the even numbers in the same order.

### **Input Format**

* First line: integer `n`.
* Second line: `n` integers.

### **Output Format**

* Print all even numbers separated by a space.
* If none are even, print `"None"`.

### **Test Cases**

1.

Input:

```
5
1 2 3 4 5
```

Output:

```
2 4
```

2.

Input:

```
4
11 13 15 17
```

Output:

```
None
```

3.

Input:

```
6
2 4 6 8 10 12
```

Output:

```
2 4 6 8 10 12
```

4.

Input:

```
1
9
```

Output:

```
None
```

5.

Input:

```
3
0 7 14
```

Output:

```
0 14
```

6.

Input:

```
7
3 6 9 12 15 18 21
```

Output:

```
6 12 18
```

7.

Input:

```
5
-2 -1 -4 0 5
```

Output:

```
-2 -4 0
```

---

## **4. Attendance Counter**

Your department keeps track of attendance for each lecture in a week. A value of `1` means present, and `0` means absent. Write a program to count how many students were present.

### **Input Format**

* First line: integer `n` (number of entries).
* Second line: `n` integers (each 0 or 1).

### **Output Format**

* Print the total count of `1`s.

### **Test Cases**

1.

Input:

```
5
1 0 1 1 0
```

Output:

```
3
```

2.

Input:

```
4
0 0 0 0
```

Output:

```
0
```

3.

Input:

```
4
1 1 1 1
```

Output:

```
4
```

4.

Input:

```
1
0
```

Output:

```
0
```

5.

Input:

```
6
1 0 0 1 0 1
```

Output:

```
3
```

6.

Input:

```
3
1 1 0
```

Output:

```
2
```

7.

Input:

```
7
0 1 0 1 0 1 0
```

Output:

```
3
```

---

## **5. Reverse the Order**

A data logger stores readings in reverse chronological order. You need to reverse them so they appear in the correct sequence.

### **Input Format**

* First line: integer `n`.
* Second line: `n` integers.

### **Output Format**

* Print the numbers in reverse order.

### **Test Cases**

1.

Input:

```
5
1 2 3 4 5
```

Output:

```
5 4 3 2 1
```

2.

Input:

```
3
10 20 30
```

Output:

```
30 20 10
```

3.

Input:

```
1
9
```

Output:

```
9
```

4.

Input:

```
4
0 0 0 0
```

Output:

```
0 0 0 0
```

5.

Input:

```
6
3 2 1 6 5 4
```

Output:

```
4 5 6 1 2 3
```

6.

Input:

```
7
9 8 7 6 5 4 3
```

Output:

```
3 4 5 6 7 8 9
```

7.

Input:

```
2
100 200
```

Output:

```
200 100
```

---

## **6. Total Sales Calculator**

A shop records daily sales in an array. You need to find the **total sales amount** for the given period.

### **Input Format**

* First line: integer `n`.
* Second line: `n` integers representing daily sales.

### **Output Format**

* Print the sum of all numbers.

### **Test Cases**

1.

Input:

```
5
10 20 30 40 50
```

Output:

```
150
```

2.

Input:

```
4
1 1 1 1
```

Output:

```
4
```

3.

Input:

```
3
100 200 300
```

Output:

```
600
```

4.

Input:

```
6
0 0 0 0 0 0
```

Output:

```
0
```

5.

Input:

```
2
-5 10
```

Output:

```
5
```

6.

Input:

```
7
5 10 15 20 25 30 35
```

Output:

```
140
```

7.

Input:

```
1
999
```

Output:

```
999
```

---

## **7. Pass or Fail Counter**

Each student’s mark is recorded in an array. A mark of 40 or above means pass. Count how many students passed and failed.

### **Input Format**

* First line: integer `n`.
* Second line: `n` integers (marks).

### **Output Format**

* Print `"Pass: X Fail: Y"`.

### **Test Cases**

1.

Input:

```
5
20 50 40 10 70
```

Output:

```
Pass: 3 Fail: 2
```

2.

Input:

```
3
40 41 39
```

Output:

```
Pass: 2 Fail: 1
```

3.

Input:

```
4
0 0 0 0
```

Output:

```
Pass: 0 Fail: 4
```

4.

Input:

```
1
80
```

Output:

```
Pass: 1 Fail: 0
```

5.

Input:

```
6
45 35 55 25 65 30
```

Output:

```
Pass: 3 Fail: 3
```

6.

Input:

```
5
100 90 80 70 60
```

Output:

```
Pass: 5 Fail: 0
```

7.

Input:

```
5
39 40 41 38 37
```

Output:

```
Pass: 2 Fail: 3
```

---

## **8. Search for a Number**

The library catalog stores book IDs in ascending order. You need to check if a given book ID exists in the list.

### **Input Format**

* First line: integer `n`.
* Second line: `n` integers.
* Third line: integer `key` to search.

### **Output Format**

* Print `"Found"` if the number exists, else `"Not Found"`.

### **Test Cases**

1.

Input:

```
5
1 2 3 4 5
3
```

Output:

```
Found
```

2.

Input:

```
4
10 20 30 40
25
```

Output:

```
Not Found
```

3.

Input:

```
3
5 5 5
5
```

Output:

```
Found
```

4.

Input:

```
6
10 20 30 40 50 60
60
```

Output:

```
Found
```

5.

Input:

```
1
100
99
```

Output:

```
Not Found
```

6.

Input:

```
7
3 6 9 12 15 18 21
9
```

Output:

```
Found
```

7.

Input:

```
5
10 20 30 40 50
100
```

Output:

```
Not Found
```

---

## **9. Sorting Exam Scores**

Your teacher wants the scores of a class arranged in ascending order before uploading them. Implement **Bubble Sort** logic to arrange the scores and display them.

### **Input Format**

* First line: integer `n`.
* Second line: `n` integers.

### **Output Format**

* Print the sorted array in ascending order.

### **Test Cases**

1.

Input:

```
5
5 3 2 4 1
```

Output:

```
1 2 3 4 5
```

2.

Input:

```
3
10 20 30
```

Output:

```
10 20 30
```

3.

Input:

```
4
9 8 7 6
```

Output:

```
6 7 8 9
```

4.

Input:

```
1
100
```

Output:

```
100
```

5.

Input:

```
6
2 2 2 2 2 2
```

Output:

```
2 2 2 2 2 2
```

6.

Input:

```
7
9 1 8 2 7 3 6
```

Output:

```
1 2 3 6 7 8 9
```

7.

Input:

```
5
0 -1 -3 5 2
```

Output:

```
-3 -1 0 2 5
```

---

## **10. Frequency Counter**

A small tool counts how many times a number appears in a dataset. Write a program that counts how often a given number appears in an array.

### **Input Format**

* First line: integer `n`.
* Second line: `n` integers.
* Third line: integer `x` (number to count).

### **Output Format**

* Print `"Frequency: k"` where `k` is the number of times `x` occurs.

### **Test Cases**

1.

Input:

```
5
1 2 3 4 5
3
```

Output:

```
Frequency: 1
```

2.

Input:

```
6
2 2 2 2 2 2
2
```

Output:

```
Frequency: 6
```

3.

Input:

```
4
5 4 3 2
1
```

Output:

```
Frequency: 0
```

4.

Input:

```
5
10 20 10 30 10
10
```

Output:

```
Frequency: 3
```

5.

Input:

```
3
-1 -1 0
-1
```

Output:

```
Frequency: 2
```

6.

Input:

```
1
9
9
```

Output:

```
Frequency: 1
```

7.

Input:

```
8
1 2 3 1 2 3 1 2
2
```

Output:

```
Frequency: 3
```

