---
- Title: "Eco-Friendly Mango Distribution" 
- Difficulty: easy
- Bloom Taxonomy: "Apply"
- Subjects: "problem-solving"
- Topics: ["sample-topic"]
- Sub Topics: ["sample-subtopic"]
- Tags: ["practice-question"]
- Company: # Keep it empty
---

### Problem Statement
The Indian government recently launched a "Green India Summer Challenge." Two friends, Aarav and Vihaan, buy the biggest organic mango at a local farmers' market. The mango weighs `w` kilos. Being eco-conscious foodies, they want to split the mango into two pieces, each weighing an even number of kilos.

However, each piece must also have positive weight, since no one wants an empty share.

Write a function to determine if it's possible for them to divide the mango this way.

### Input Format
A single integer `w` representing the weight of the mango in kilos.

### Output Format
Return `true` if it's possible to divide the mango into two pieces where each piece has positive even weight, otherwise return `false`.

### Constraints
- 1 ≤ w ≤ 10^9
- w is a positive integer

---

**Test Case 1**

Input:
```
6
```

Output:
```
true
```

Explanation:
```
The mango weighs 6 kilos. We can split it into 2 kilos and 4 kilos. Both pieces are positive and even, so the answer is true.
```

**Test Case 2**

Input:
```
4
```

Output:
```
true
```

Explanation:
```
The mango weighs 4 kilos. We can split it into 2 kilos and 2 kilos. Both pieces are positive and even, so the answer is true.
```

**Test Case 3**

Input:
```
3
```

Output:
```
false
```

Explanation:
```
The mango weighs 3 kilos. Any split would be (1,2) or similar. Since 1 is odd, we cannot have both pieces as even numbers.
```

**Test Case 4**

Input:
```
2
```

Output:
```
false
```

Explanation:
```
The mango weighs 2 kilos. The only way to split with positive weights is (1,1), but 1 is odd, so the answer is false.
```

**Test Case 5**

Input:
```
8
```

Output:
```
true
```

Explanation:
```
The mango weighs 8 kilos. We can split it into 2 kilos and 6 kilos, or 4 kilos and 4 kilos. Both splits have positive even pieces.
```

**Test Case 6**

Input:
```
10
```

Output:
```
true
```

Explanation:
```
The mango weighs 10 kilos. We can split it into 2 kilos and 8 kilos, or 4 kilos and 6 kilos. Both pieces are positive and even.
```

**Test Case 7**

Input:
```
1
```

Output:
```
false
```

Explanation:
```
The mango weighs 1 kilo. We cannot split it into two positive pieces since any split would result in at least one piece being 0 or negative.
```

---

## Python Solution

```python
def compute(w):
    # For two even numbers to sum to w, w must be even
    # Also, w must be at least 4 to allow two positive even numbers (2+2=4)
    return w >= 4 and w % 2 == 0

w = int(input())
result = compute(w)
print("true" if result else "false")
```

## Java Solution

```java
import java.util.*;

public class Main {
    public static boolean canDivideMango(int w) {
        // For two even numbers to sum to w, w must be even
        // Also, w must be at least 4 to allow two positive even numbers (2+2=4)
        return w >= 4 && w % 2 == 0;
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int w = sc.nextInt();
        boolean result = canDivideMango(w);
        System.out.println(result ? "true" : "false");
        sc.close();
    }
}
```

## C++ Solution

```cpp
#include <iostream>
using namespace std;

bool canDivideMango(int w) {
    // For two even numbers to sum to w, w must be even
    // Also, w must be at least 4 to allow two positive even numbers (2+2=4)
    return w >= 4 && w % 2 == 0;
}

int main() {
    int w;
    cin >> w;
    bool result = canDivideMango(w);
    cout << (result ? "true" : "false") << endl;
    return 0;
}
```
