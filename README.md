# Pre-Session-Assignment-InterviewCafe

# Part 2 : Problem-Solving Reflection

# Problem 1 : Two Sum

### 1. What was your first thought after reading the problem?
I thought of checking every possible pair of elements and seeing whether their sum equals the target.

### 2. What brute-force solution came to your mind?
Use two nested loops.
* Pick the first element using index `i`.
* For every `i`, check all elements after it using index `j`.
* If `nums[i] + nums[j] == target`, store the indices and return them.

### 3. What is the time complexity of your solution?
* **Time Complexity:** `O(n²)`
* **Space Complexity:** `O(1)`

### 4. Can you think of a better solution?
**YES**
#### Intuition:
While traversing the array, for each element `nums[i]`, calculate the required value
`rem = target - nums[i]`
If this required value has already appeared earlier, then we have found the answer.
To quickly check whether the required value exists, store previously visited elements and their indices in a HashMap.
This avoids checking every pair.

### 5. Where do you think optimization is possible?
* Repeated searches inside the inner loop.
* Extra loop causing duplicate work.
* Checking all pairs even though only one matching pair is needed.
* Using a HashMap allows constant-time lookup and eliminates the nested loop.

### Optimized Solution
* Traverse the array once.
* For each number, compute `target - nums[i]`.
* If this value exists in the HashMap, return the stored index and the current index.
* Otherwise, insert the current number and its index into the map.

**Time Complexity:** `O(n)`
**Space Complexity:** `O(n)`

# Problem 2 : Longest Substring Without Repeating Characters

### 1. What was your first thought after reading the problem?
I thought of checking every possible substring and verifying whether all characters in that substring are distinct.

### 2. What brute-force solution came to your mind?
Generate all possible substrings.
For each substring:
Use a set or frequency array to check whether any character repeats.
If all characters are unique, update the maximum length.

Finally, return the length of the longest valid substring.

### 3. What is the time complexity of your solution?
For the brute-force approach:
Time Complexity: O(n³)
O(n²) substrings.
O(n) to check uniqueness of each substring.
Space Complexity: O(n)

### 4. Can you think of a better solution?
YES
Intuition:
Instead of recomputing every substring, maintain a sliding window containing only unique characters.
As we extend the window by moving j, if the current character has already appeared inside the window, move the left pointer i to one position after its previous occurrence.
Store the most recent index of each character in a HashMap so that duplicate characters can be detected quickly.
This way, every character is processed only once.

### 5. Where do you think optimization is possible?
Repeatedly checking the same characters in overlapping substrings.
Generating all possible substrings unnecessarily.
Recomputing uniqueness from scratch for every substring.
Extra nested loops causing duplicate work.
Using a HashMap and sliding window allows direct jumps to the next valid position instead of moving one step at a time.
Optimized Solution (Your Code)
Maintain a window [i, j] containing distinct characters.
Store the latest index of each character in a HashMap.
When a duplicate character is found within the current window, move i to map.get(ch) + 1.
Update the character's latest index and continue expanding the window.
Keep track of the maximum window length encountered.
Time Complexity: O(n)
Space Complexity: O(min(n, charset size)) (at most O(n))

# Problem 3 : Climbing Stairs 

### **1. What was your first thought after reading the problem?**

I thought that to reach the nth stair, I could either come from the `(n-1)`th stair by taking one step or from the `(n-2)`th stair by taking two steps.

### **2. What brute-force solution came to your mind?**
Use recursion.
For every stair `n`:
* Find the number of ways to reach stair `n-1`.
* Find the number of ways to reach stair `n-2`.
* Add both values to get the answer for stair `n`.
Continue recursively until reaching the base cases `n = 1` and `n = 2`.

### **3. What is the time complexity of your solution?**
### Brute-force Recursive Solution
* **Time Complexity:** `O(2ⁿ)`
* **Space Complexity:** `O(n)` (recursion stack)

### **4. Can you think of a better solution?**
**YES**
### Intuition:
The recursive solution repeatedly computes the same subproblems.
For example, while computing `climbStairs(5)`, the values of `climbStairs(4)`, `climbStairs(3)`, and `climbStairs(2)` are calculated multiple times.
If we store previously computed answers, we can avoid these repeated calculations.
This leads to Dynamic Programming.

### **5. Where do you think optimization is possible?**
* Repeated recursive calls.
* Solving the same subproblems multiple times.
* Excessive recursion.
* Extra memory used by the recursion stack.
* Storing intermediate results and computing iteratively.

### **Memoization (Top-Down DP)**
Store the answer for each value of `n` in a HashMap.
Before computing `climbStairs(n)`, check whether it has already been calculated.
This eliminates repeated recursive calls.
* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(n)`

### **Further Optimization**
Since each state depends only on the previous two states, we do not need to store all values.
Maintain only two variables representing the answers for the previous two stairs and update them iteratively.
This gives:
* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(1)`

### Progression of solutions
1. **Brute Force Recursion** → `O(2ⁿ)`
2. **Memoization (Top-Down DP)** → `O(n)` time, `O(n)` space
3. **Iterative DP with Two Variables** → `O(n)` time, `O(1)` space


