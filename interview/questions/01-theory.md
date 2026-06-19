# Data Structures and Algorithms

This is the foundation of every SWE coding interview. I organized the most frequently tested topics based on analysis of interview question databases, candidate reports, and company-specific question tags. For each category, I included real questions with the expected complexity analysis and common patterns interviewers look for.

## Arrays and Strings

Arrays and strings appear in virtually every coding interview. They are the most common first question because they test fundamental manipulation skills without requiring specialized data structure knowledge.

Common patterns: sorting and comparing, in-place modification, prefix sums, kadane's algorithm for subarray problems.

Questions:
1. Two Sum: given an array of integers and a target, return indices of two numbers that add up to the target. Expected: O(n) time, O(n) space using a hash map. Follow-up: what if the array is sorted?
2. Best Time to Buy and Sell Stock: find the maximum profit from one buy and one sell. Expected: O(n) time, O(1) space with a running minimum.
3. Maximum Subarray (Kadane's): find the contiguous subarray with the largest sum. Expected: O(n) time, O(1) space.
4. Product of Array Except Self: return an array where each element is the product of all other elements without using division. Expected: O(n) time, O(1) extra space using prefix and suffix products.
5. Longest Substring Without Repeating Characters: find the length of the longest substring with all unique characters. Expected: O(n) time using sliding window with a hash set.
6. Valid Anagram: determine if two strings are anagrams. Expected: O(n) time using character frequency counting.
7. Group Anagrams: group strings that are anagrams of each other. Expected: O(n * k log k) time where k is max string length. Alternative: O(n * k) using character count as key.
8. Merge Intervals: merge overlapping intervals. Expected: O(n log n) time for sorting, O(n) space. Watch for edge cases with single-element intervals.

## Hash Maps and Sets

Hash-based data structures are the most commonly used tool in coding interviews. If you are stuck on a problem, ask yourself whether a hash map can help. About 40.0% of the time, it can.

Common patterns: frequency counting, two-pass lookup, grouping by key, detecting duplicates.

Questions:
1. Contains Duplicate: determine if any value appears at least twice. Expected: O(n) time, O(n) space.
2. Valid Sudoku: determine if a 9x9 board is valid. Expected: O(1) time (fixed size), using sets for rows, columns, and boxes.
3. Longest Consecutive Sequence: find the length of the longest consecutive element sequence. Expected: O(n) time using a hash set and only starting count from sequence beginnings.
4. Top K Frequent Elements: return the k most frequent elements. Expected: O(n) time using bucket sort or O(n log k) using a min-heap.
5. Isomorphic Strings: determine if two strings are isomorphic. Expected: O(n) time with two hash maps for bidirectional mapping.
6. Minimum Window Substring: find the smallest window in a string containing all characters of another string. Expected: O(n) time using sliding window with character frequency maps.

## Linked Lists

Linked list questions test pointer manipulation and edge case handling. They are less common than array questions but still appear regularly, especially at companies like Amazon and Microsoft.

Common patterns: fast and slow pointers, reversal, merge, dummy head node.

Questions:
1. Reverse a Linked List: reverse iteratively and recursively. Expected: O(n) time, O(1) space iteratively.
2. Detect Cycle: determine if a linked list has a cycle. Expected: O(n) time, O(1) space using Floyd's tortoise and hare algorithm. Follow-up: find the cycle start node.
3. Merge Two Sorted Lists: merge two sorted linked lists into one. Expected: O(n + m) time, O(1) space.
4. Remove Nth Node From End: remove the nth node from the end in one pass. Expected: O(n) time using two pointers with n gap.
5. Reorder List: reorder L0 to L1 to Ln to Ln-1 to L1 to Ln-1... Expected: O(n) time using find middle, reverse second half, merge.
6. LRU Cache: design a least recently used cache with O(1) get and put. Expected: hash map plus doubly linked list.

## Stacks and Queues

Stack questions test LIFO logic and are particularly common for parsing and expression evaluation problems. Queue questions often involve BFS.

Common patterns: monotonic stack, matching brackets, next greater element, BFS with queue.

Questions:
1. Valid Parentheses: determine if a string of brackets is valid. Expected: O(n) time, O(n) space.
2. Min Stack: design a stack that supports push, pop, top, and retrieving the minimum element in O(1). Expected: auxiliary stack tracking minimums.
3. Evaluate Reverse Polish Notation: evaluate an arithmetic expression in RPN. Expected: O(n) time using a stack.
4. Daily Temperatures: for each day, find how many days until a warmer temperature. Expected: O(n) time using a monotonic decreasing stack.
5. Implement Queue Using Stacks: implement a FIFO queue using two stacks. Expected: amortized O(1) per operation.
6. Next Greater Element: for each element, find the next greater element to the right. Expected: O(n) time using a monotonic stack.

## Trees and Graphs

Trees and graphs are among the most heavily tested topics. BFS and DFS are fundamental techniques that apply to many problem types.

Common patterns: recursive traversal, level-order traversal, path problems, lowest common ancestor, graph coloring, topological sort.

Questions:
1. Maximum Depth of Binary Tree: find the maximum depth. Expected: O(n) time, either recursive DFS or iterative BFS.
2. Validate Binary Search Tree: determine if a tree is a valid BST. Expected: O(n) time using in-order traversal or min/max bounds.
3. Lowest Common Ancestor of BST: find the LCA of two nodes. Expected: O(h) time where h is height, using BST property.
4. Binary Tree Level Order Traversal: return values level by level. Expected: O(n) time using BFS with queue.
5. Serialize and Deserialize Binary Tree: design an algorithm to serialize and deserialize a binary tree. Expected: O(n) time using pre-order traversal.
6. Number of Islands: count the number of islands in a 2D grid. Expected: O(m * n) time using BFS or DFS.
7. Clone Graph: deep copy a graph. Expected: O(V + E) time using BFS or DFS with a hash map to track visited nodes.
8. Course Schedule: determine if you can finish all courses given prerequisites. Expected: O(V + E) time using topological sort (BFS with in-degree or DFS with cycle detection).

## Sorting and Searching

Sorting algorithms are rarely asked to implement from scratch, but understanding their properties and knowing binary search variations is essential.

Common patterns: binary search variations, merge sort for linked lists, quick select for kth element.

Questions:
1. Binary Search: implement binary search on a sorted array. Expected: O(log n) time. Watch for off-by-one errors with inclusive vs exclusive bounds.
2. Search in Rotated Sorted Array: find a target in a rotated sorted array. Expected: O(log n) time using modified binary search.
3. Find Minimum in Rotated Sorted Array: find the minimum element. Expected: O(log n) time.
4. Kth Largest Element: find the kth largest element in an unsorted array. Expected: O(n) average time using quick select, O(n log k) using a min-heap.
5. Median of Two Sorted Arrays: find the median of two sorted arrays. Expected: O(log(min(m,n))) time using binary search on the smaller array.
6. Search a 2D Matrix: search for a value in a row-sorted, column-sorted matrix. Expected: O(m + n) time starting from top-right or bottom-left corner.

## Recursion and Backtracking

Backtracking questions test your ability to explore solution spaces systematically. They are common at Google and Meta.

Common patterns: generate all combinations/permutations, constraint satisfaction, pruning.

Questions:
1. Subsets: generate all subsets of a set. Expected: O(2^n) time and space.
2. Permutations: generate all permutations. Expected: O(n! * n) time.
3. Combination Sum: find all combinations that sum to a target. Expected: backtracking with pruning.
4. N-Queens: place n queens on an n x n board. Expected: backtracking with column, diagonal, and anti-diagonal tracking.
5. Word Search: find if a word exists in a 2D grid. Expected: O(m * n * 4^L) time where L is word length.
6. Letter Combinations of a Phone Number: generate all letter combinations. Expected: O(4^n) time where n is digit count.

## Dynamic Programming

DP questions are considered the hardest category. They test pattern recognition and the ability to break problems into overlapping subproblems.

Common patterns: 1D DP, 2D DP, knapsack variations, string DP, interval DP.

Questions:
1. Climbing Stairs: count ways to climb n stairs taking 1 or 2 steps at a time. Expected: O(n) time, O(1) space with two variables.
2. Coin Change: find the minimum number of coins for an amount. Expected: O(amount * coins) time.
3. Longest Increasing Subsequence: find the length of the LIS. Expected: O(n log n) time using patience sorting or O(n^2) with basic DP.
4. Longest Common Subsequence: find the LCS of two strings. Expected: O(m * n) time and space, reducible to O(min(m,n)) space.
5. Word Break: determine if a string can be segmented into dictionary words. Expected: O(n^2) time.
6. Edit Distance: find minimum edits to transform one string to another. Expected: O(m * n) time and space.
7. House Robber: maximize robbery amount without robbing adjacent houses. Expected: O(n) time, O(1) space.
8. Unique Paths: count paths in a grid from top-left to bottom-right. Expected: O(m * n) time.

## Greedy Algorithms

Greedy questions require proving that a local optimal choice leads to a global optimum. They appear less frequently than DP but are important to recognize.

Questions:
1. Jump Game: determine if you can reach the last index. Expected: O(n) time using greedy rightmost reachable position.
2. Gas Station: find the starting gas station to complete a circuit. Expected: O(n) time.
3. Task Scheduler: find the minimum intervals to complete all tasks with a cooldown. Expected: O(n) time using frequency counting.
4. Non-overlapping Intervals: find the minimum number of intervals to remove. Expected: O(n log n) time after sorting by end time.
5. Partition Labels: partition a string so each letter appears in at most one part. Expected: O(n) time using last occurrence tracking.

## Bit Manipulation

Bit manipulation questions test low-level thinking. They are less common but still appear, especially at companies that work on systems-level code.

Questions:
1. Single Number: find the element that appears only once (all others appear twice). Expected: O(n) time, O(1) space using XOR.
2. Number of 1 Bits: count set bits. Expected: O(1) time with Brian Kernighan's algorithm.
3. Counting Bits: for every number 0 to n, count the number of 1 bits. Expected: O(n) time using DP.
4. Reverse Bits: reverse bits of a 32-bit integer. Expected: O(1) time.
5. Missing Number: find the missing number in range 0 to n. Expected: O(n) time using XOR or sum formula.

## Math and Logic

Pure math questions are uncommon but not unheard of. They test analytical thinking more than coding skill.

Questions:
1. Fizz Buzz: classic screening question. Expected: O(n) time. Interviewers watch for clean code structure.
2. Power of Two: determine if a number is a power of two. Expected: O(1) time using n & (n-1) == 0.
3. Roman to Integer: convert a Roman numeral string to an integer. Expected: O(n) time.
4. Happy Number: determine if a number eventually reaches 1 through sum of squares of digits. Expected: Floyd's cycle detection.
5. Rotate Image: rotate an n x n matrix 90 degrees in-place. Expected: O(n^2) time, transpose then reverse rows.

## How to Use This Section

Do not try to memorize solutions. Instead, focus on recognizing which pattern applies to each problem. When you see a new problem, ask: have I seen something structurally similar? What data structure would simplify this? Can I reduce it to a known problem?

I recommend solving 3-5 problems per category, focusing on understanding the pattern rather than memorizing the code. When you can look at a new problem and say "this is a sliding window problem" or "this needs monotonic stack," you are ready.
