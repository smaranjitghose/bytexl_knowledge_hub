# Trionic Array I: The Pilgrim’s Sacred Journey

In the ancient Valley of Numbers, a pilgrim embarks on a sacred journey — one that must follow the divine rhythm of ascent, descent, and rebirth.

You are given an integer array `nums` of length `n`, representing the elevation at each step along the pilgrim’s path.

Your task is to determine if there exists a sacred route through this land — defined by two turning shrines `p` and `q` (where `0 < p < q < n − 1`) — that divides the journey into three holy phases:

1. The Ascent to the First Peak (0 to p):  
   The pilgrim climbs — each step higher than the last. No plateau. No fall. Strictly upward.

2. The Descent into the Sacred Valley (p to q):  
   From the peak, the pilgrim descends — each step lower than the one before. No rise. No rest. Strictly downward.

3. The Rebirth Climb to the Final Horizon (q to end):  
   From the valley’s depth, the pilgrim rises again — ascending with purpose to the journey’s end. Strictly upward once more.

If such a path exists — where the pilgrim rises, falls, then rises again — return `true`. The land is Trionic, blessed with the rhythm of balance.

If no such shrines `p` and `q` can be found — return `false`. The path is incomplete. The pilgrim cannot fulfill the sacred cycle.

---

## Constraints

- `4 <= nums.length <= 1000`
- `1 <= nums[i] <= 1000`

---

## Test Cases

### Test Case 1
**Input:** `nums = [1,3,5,4,2,6]`  
**Output:** `true`  
**Explanation:**  
Shrine `p = 2` (peak at 5), Shrine `q = 4` (valley at 2)  
- Ascent: [1 → 3 → 5]  
- Descent: [5 → 4 → 2]  
- Rebirth: [2 → 6]  
The Pilgrim completes the Sacred Journey.

---

### Test Case 2
**Input:** `nums = [1,2,3,4,5]`  
**Output:** `false`  
**Explanation:**  
Only ascent — no valley, no rebirth. The pilgrim never descends. The cycle is broken.

---

### Test Case 3
**Input:** `nums = [5,4,3,2,1]`  
**Output:** `false`  
**Explanation:**  
Only descent — no rebirth. The pilgrim falls endlessly, never rising again.

---

### Test Case 4
**Input:** `nums = [1,4,2,3,5]`  
**Output:** `true`  
**Explanation:**  
Shrine `p = 1` (peak at 4), Shrine `q = 2` (valley at 2)  
- Ascent: [1 → 4]  
- Descent: [4 → 2]  
- Rebirth: [2 → 3 → 5]  
The Pilgrim finds balance.

---

### Test Case 5
**Input:** `nums = [2,1,3,4,5]`  
**Output:** `false`  
**Explanation:**  
The pilgrim begins by falling — violating the First Law of Ascent. No shrine `p > 0` can redeem the start.

---

### Test Case 6
**Input:** `nums = [1,5,3,6,4,7]`  
**Output:** `false`  
**Explanation:**  
Every attempted path breaks the sacred rules:  
- After descent, a false rise breaks the valley.  
- After valley, a dip breaks the rebirth.  
No true turning shrines exist.

---

### Test Case 7
**Input:** `nums = [1,5,4,3,6,7]`  
**Output:** `true`  
**Explanation:**  
Shrine `p = 1` (peak at 5), Shrine `q = 3` (valley at 3)  
- Ascent: [1 → 5]  
- Descent: [5 → 4 → 3]  
- Rebirth: [3 → 6 → 7]  
The Pilgrim completes the Trionic Cycle. The land is blessed.


```
