# Data Structures and Algorithms in C and C++
These notes are taken from the Udemy course [Mastering Data Structures & Algorithms using C and C++](https://www.udemy.com/course/datastructurescncpp/), taught by Professor Abdul Bari.

## Background Knowledge for DSA
### Abstract Data Types (ADT)
- A data type is defined in two ways
    - How the data is represented
    - What operations are allowed on that data
-	Abstract data types are heavily used in object-oriented programming
-	The “abstract” part means that we don’t care how the data type is implemented. We just care about its purpose and how we can use it in our programs.
-	An example of an abstract data type would be a list of numbers and the things you can do to that list of numbers, like:
    - Adding an element anywhere in the list
    - Removing an element
    - Finding an element
    - Summing all the elements
### Time and Space Complexity
-	To determine complexity, consider in order:
    - The number of elements to be operated on to get an answer
    - The operation intended for each element
    - How many times that operation will have to happen to get your answer
-	Complexity of O(n)
    - Searching for an element in an array
    - Adding all the elements of an array
    - Processing a row of elements in a matrix (2-D array)
-	Complexity of O(n^2)
    - Sorting elements in an array
    - Processing all the elements in a matrix (2-D array)
-	If you have a nested for loop, you likely have a time complexity of O(n^2)
-	To find time complexity, look at how many times a loop iterates
    - If that loop has a loop inside of it, the outermost loop will iterate n times, and the inner loop will iterate n times, n times. Get it? So its time complexity is n^2.
-	For procedures that successively cut the number of elements to process in half, the time complexity is usually O(log2n), because it is the direct opposite of a procedure that takes n^2 time.
- When choosing an algorithm: 
  - To reduce the time taken, you likely need to use more memory space (hash table, memoization).
  - To reduce the memory space used, you'll likely have to use a more time-consuming algorithm (nested loops)
## Recursion
### How recursion works
-	For recursion to work, there must be a base case that ends the recursive process
    - Use an if statement
-	You can trace a recursive function with a tree, with the output on one limb and the next call on the other limb
-	Once a recursive function call terminates, control returns back to exactly the line it was called at in the previous recursive call.
-	Example: Turning on lightbulbs in room
    - There are three rooms, each with a lightbulb in them, and the rooms are marked 1 thru 3 from left to right.
    - The base case would be if you reach a wall with no door, go back to the previous room
    - The two instructions:
        - Go to next room
        - Turn on the room’s lightbulb
    - The order in which the bulbs are turned on depends on the order of the instructions.
    - If “turn on bulb” is the first instruction, the bulbs will be lit in the order 1 -> 2 -> 3.
    - If “go to next room” is the first instruction, the bulbs will be lit 3 -> 2 -> 1.
-	Any expressions before the recursive function call happen at calling time (ascending phase).
-	Any expressions after the recursive function call happen at retuning time (descending phase).
-	Loops only have an ascending phase; recursion has both ascending and descending phases.
### How recursion uses the stack
1.	Program code is loaded into the code section of the main memory
2.	A stack frame (activation record) is created for the main function in the stack section of the main memory
3.	For each call of the recursive function, a new stack frame (activation record) is created for that specific call with the updated variable that’s to be checked against the base case.
4.	As each recursive function call completes, the respective activation record for that call is deleted from the stack.
-	The total number of activation records or recursive function calls are (n + 1), where n is the variable that the base case checks.
-	The minimum amount of memory used by a recursive function is the size of n multiplied by the number of calls (n + 1).
### Global and static variables in recursive functions
-	Recursive function calls, like fun(n - 1) + n, result in n being updated with every recursive call.
    - In fun(), there will be n number of copies of the variable n created in the stack
-	If we replace fun(n-1) + n with fun(n-1) + x, where x is a static or global variable:
    - Only one copy of x will be created
    - The variable x will be located in the code section of main memory, not the stack
### Types of recursion
-	Tail recursion
    - When a recursive function makes its recursive call to itself at the end of the function definition
    - All operations happen at calling time
    - Tail-recursive functions can be converted into while functions
        - While loops generally have better space efficiency than tail-recursive functions
-	Head recursion
    - First statement in the recursive function is a recursive call to itself.
    - No operations happen at calling time; all operations happen at returning time
-	Linear recursion
    - When a function calls itself recursively just once
-	Tree recursion
    - When a function calls itself recursively two or more times.
    - When analyzing a tree recursive call, you create a tree diagram and read the calls from left to right, top to bottom
-	Indirect recursion
    - When function A calls function B, and then function B calls function A.
    - There can be more than two functions in indirect recursion, but the general pattern must start and stop with the first function (it’s gotta be cyclical)
-	Nested recursion
    - When a function calls itself recursively, and that recursive call takes a recursive call to itself as a parameter
    - Example: `fun(fun(n+1));`
#### Memoization in recursive functions
-	Tree recursive functions can make many of the same calls (for example, a Fibonacci sum finder function), known as excessive recursion
-	Memoization is when you store the results of function calls for later use.
    - With Fibonacci, you store the sums returned by previous recursive calls and use them to avoid calling the same function over and over.
-	In C, a function’s results can be stored in an array or linked list.
## Array Representations/Array ADT
- 2D arrays are allocated in the same way as single dimensional arrays: in contiguous blocks of memory.
- To create a 2D array in the stack:
```c
int A[3][4];
// Creates an integer array with 3 rows and 4 columns
```
- To create a 2D array using the stack and the heap:
```c
// C
int *A[3];

A[0] = (int *) malloc(4 * sizeof(int));
A[1] = (int *) malloc(4 * sizeof(int));
A[2] = (int *) malloc(4 * sizeof(int));

// Uses an array of pointers to point to memory locations in the heap.
```
```cpp
// C++
int *A[3];

A[0] = new int[4];
A[1] = new int[4];
A[2] = new int[4];
```
- To create a 2D array using only the heap:
```c
// C
int **A;

A = (int **) malloc(3 * sizeof(int *));

A[0] = (int *) malloc(4 * sizeof(int));
A[1] = (int *) malloc(4 * sizeof(int));
A[2] = (int *) malloc(4 * sizeof(int));
```
```cpp
// C++
int **A;

A = new int*[3];

A[0] = new int[4];
A[1] = new int[4];
A[2] = new int[4];
```

- Row-major mapping is when a 2D array addresses elements in the array based on which row they're in
- Column-major mapping is when elements are mapped based on which column they're in


__2D Array A[3][4]__
|   | 0   | 1   | 2   | 3   |
|---|-----|-----|-----|-----|
| 0 | A00 | A01 | A02 | A03 |
| 1 | A10 | A11 | A12 | A13 |
| 2 | A20 | A21 | A22 | A23 |

__2D Array A[3][4], row-mapped__

| address | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  | 11  |
|---------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| value   | A00 | A01 | A02 | A03 | A10 | A11 | A12 | A13 | A20 | A21 | A22 | A23 |


__2D Array A[3][4], column-mapped__

| address | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  | 11  |
|---------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| value   | A00 | A10 | A20 | A01 | A11 | A21 | A02 | A12 | A22 | A03 | A13 | A23 |


- C and C++ follow row-major mapping.

### Array ADT
- ADT = Abstract data type
    - An array as an ADT is a group of data items and the operations you can perform on them

#### Array Operations
- display(array)
- add(x)/append(x)
- insert(index,x)
- search(x)
- delete(index)
- get(index)
  - O(1) time complexity
- set(index, x)
  - O(1) time complexity
- max(array)/min(array)
  - O(n) time complexity
- sum(array)
  - O(n) time complexity
- average(array)
  - O(n) time complexity
- reverse(array)
  - O(n) time complexity
- shift(array)/rotate(array)
  - O(n) time complexity

### Array Search Methods

1. Linear search
2. Binary search

#### Linear search

- Key = search term
- Checks elements one by one, front to back.
- Linear search functions have to handle whether the key is found or not found.
  - Return the index when the key is found.
  - Return -1 when it isn't found (arrays don't have negative indecies).
- To implement a linear search, use a for loop.
    - i starts at 0
    - i < length
    - i++ every time the loop runs
- Time complexity of linear search
    - min = O(1)
    - max = O(n)
    - avg = O(n)
- In general, use worst case analysis to determine an algorithm's efficiency.

- Ways to improve linear search
    - Move the search key up one index each time it's searched for (transposition)
    - Swap the first element of the array with the search key (move-to-front)


#### Binary Search

- Binary search can only be used on a sorted array (least to greatest)
- To start, always check for key in middle of list
    - Splits list in 2: greater than key and lower than key
- Binary search uses three index variables:
    - low = beginning of array
    - high = end index of array
    - middle = (low + high) / 2
- After comparing the search key to the middle:
    - if middle is greater, update low = middle + 1.
    - if middle is less, update high = middle - 1
- Repeat the compare-then-cut-in-half process until key is found
- When low is greater than high, stop searching. The key isn't in the list.
- Implement a binary search using a loop
  - Can be implemented with recursion, but that uses the stack and is less efficient
- Time complexity analysis
  - Best case: O(1)
  - Worst case: O(log(n))

### Sorting arrays
- To sort an array, start at front and check each element against the one after it
- Time complexity: O(n)

### Merging arrays
- Merge is a binary operation (meaning you need two arrays)
- Other binary operations on arrays include:
  - Append
  - Concat
  - Compare
  - Copy
  - merge
- Merging only sorted
- need a third array
- compare two elements, store smaller one first, then move indecies
  - if leftovers, add them to end of third array
- Time complexity: O(m+n)
  - m variable is used in merging

### Set operations on arrays
- Set operations are binary operations, like merge
  - Union
  - Intersection
  - Difference
  - Set membership
- Union
  - copy elements of arr1 then copy elements of arr2, but don't duplicate
  - Union time complexity (unsorted sets): O(n^2)
  - Sorted sets can use merge instead of union
  - Union time complexity (sorted sets): O(n) or O(m+n)
- Intersection
  - Take common elements only
  - Time complexity (unsorted): O(n^2)
  - Time complexity (sorted): O(n);
    - You can use an algorithm similar to merge for sorted intersection
  - Difference
    - Only take elements that are only in array A, not in both A and B
    - Time complexity (unsorted): O(n^2)
    - Time complexity (sorted): O(n)
  - Set membership
    - Same procedure as search


