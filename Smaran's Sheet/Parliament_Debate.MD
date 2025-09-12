---

* Title: "Parliament Debate: NDA vs UPA"
* Difficulty: medium
* Bloom Taxonomy: "Apply"
* Subjects: "dsa"
* Topics: []
* Sub Topics:[]
* Tags: []

---

### Problem Statement

During a fiery session of the **Indian Parliament**, MPs from two alliances — **NDA (N)** and **UPA (U)** — are debating a controversial bill.

The Speaker gives MPs turns in the order they are seated (left to right). On their turn:

1. An MP can **silence** one opponent so that the opponent cannot speak again in the session.
2. If at any moment, all MPs who can still speak belong to the same alliance, that alliance **claims victory** in the debate.

All MPs act optimally for their own alliance.

Your task is to predict **which alliance will eventually win**.

---

### Input Format

* A single string `parliament` consisting only of the characters `'N'` and `'U'`.

### Output Format

* Print `"NDA"` if the NDA alliance eventually wins, otherwise print `"UPA"`.

---

### Constraints

* `1 <= len(parliament) <= 10^4`
* `parliament[i] ∈ {'N', 'U'}`

---

### Test Cases

**Test Case 1**
Input:

```
N
```

Output:

```
NDA
```

**Test Case 2**
Input:

```
NU
```

Output:

```
NDA
```

**Test Case 3**
Input:

```
NUU
```

Output:

```
UPA
```

**Test Case 4**
Input:

```
NUNU
```

Output:

```
NDA
```

**Test Case 5**
Input:

```
UUUN
```

Output:

```
UPA
```

**Test Case 6**
Input:

```
NNUUU
```

Output:

```
UPA
```

**Test Case 7**
Input:

```
NUUNNU
```

Output:

```
NDA
```

---

## Python Solution

```python
from collections import deque

def compute(parliament: str) -> str:
    n = len(parliament)
    qN, qU = deque(), deque()

    for i, ch in enumerate(parliament):
        if ch == 'N':
            qN.append(i)
        else:
            qU.append(i)

    while qN and qU:
        ni = qN.popleft()
        ui = qU.popleft()
        if ni < ui:
            qN.append(ni + n)
        else:
            qU.append(ui + n)

    return "NDA" if qN else "UPA"

s = input().strip()
print(compute(s))
```

---

## Java Solution

```java
import java.util.*;

public class Main {
    public static String compute(String parliament) {
        int n = parliament.length();
        Deque<Integer> qN = new ArrayDeque<>();
        Deque<Integer> qU = new ArrayDeque<>();

        for (int i = 0; i < n; i++) {
            if (parliament.charAt(i) == 'N') qN.addLast(i);
            else qU.addLast(i);
        }

        while (!qN.isEmpty() && !qU.isEmpty()) {
            int ni = qN.removeFirst();
            int ui = qU.removeFirst();
            if (ni < ui) qN.addLast(ni + n);
            else qU.addLast(ui + n);
        }

        return qN.isEmpty() ? "UPA" : "NDA";
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine().trim();
        System.out.println(compute(s));
        sc.close();
    }
}
```

---

## C++ Solution

```cpp
#include <bits/stdc++.h>
using namespace std;

string compute(const string& parliament) {
    int n = (int)parliament.size();
    queue<int> qN, qU;

    for (int i = 0; i < n; ++i) {
        if (parliament[i] == 'N') qN.push(i);
        else qU.push(i);
    }

    while (!qN.empty() && !qU.empty()) {
        int ni = qN.front(); qN.pop();
        int ui = qU.front(); qU.pop();
        if (ni < ui) qN.push(ni + n);
        else qU.push(ui + n);
    }
    return qN.empty() ? "UPA" : "NDA";
}

int main() {
    string s;
    cin >> s;
    cout << compute(s) << "\n";
    return 0;
}
```
