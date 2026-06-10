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
