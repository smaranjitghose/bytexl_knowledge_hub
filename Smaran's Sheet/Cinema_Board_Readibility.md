# Cinema Board Readibility

In an Indian town, the cinema’s neon signboard has some malfunctioning lights. Certain letters do not glow, which makes it impossible to read any movie title that contains those broken letters.  

You are given a string `titles` containing movie names separated by a single space (no leading or trailing spaces), and a string `brokenLetters` containing all distinct letters of the English alphabet whose neon lights are broken.  

Return the number of movie titles that can still be fully read from the board.  


## Constraints:
- `1 <= titles.length <= 10^4`  
- `0 <= brokenLetters.length <= 26`  
- `titles` consists of movie names separated by a single space without leading or trailing spaces.  
- Each title only consists of lowercase English letters.  
- `brokenLetters` consists of distinct lowercase English letters.  

---

## Test Cases:


#### Test Case 1

**Input:**  
`titles = "sholay dhoom krrish", brokenLetters = "ay"`  
**Output:**  
`1`  

#### Test Case 2

**Input:**  
`titles = "pathaan lagaan swades", brokenLetters = ""`  
**Output:**  
`3`  

#### Test Case 3

**Input:**  
`titles = "kgf bahubali pushpa", brokenLetters = "apbghfluiosk"`  
**Output:**  
`0`  

#### Test Case 4

**Input:**  
`titles = "rrr", brokenLetters = "z"`  
**Output:**  
`1`  

#### Test Case 5

**Input:**  
`titles = "dangal chakde lagaan", brokenLetters = "dgn"`  
**Output:**  
`1`  

#### Test Case 6

**Input:**  
`titles = "shershaah lunchbox queen drishyam gangubai masaan highway uri pink airlift", brokenLetters = "u"`  
**Output:**  
`7`  

#### Test Case 7

**Input:**  
`titles = "golmaal", brokenLetters = "abcdefghijklmnopqrstuvwxyz"`  
**Output:**  
`0`  
