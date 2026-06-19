# Coding Challenges and Patterns

LeetCode-style coding interviews follow recognizable patterns. I analyzed the most frequently tested patterns across interview question databases, candidate reports, and company-specific question lists. Mastering these 14 patterns covers roughly 80.0% of coding problems you will encounter.

## The Interview Format

A typical coding round lasts 45-60 minutes and follows this structure:
- 5 minutes: introductions, problem statement
- 5-10 minutes: clarifying questions, discuss approach
- 25-35 minutes: write code
- 5-10 minutes: test, edge cases, complexity analysis

You are usually expected to solve 1-2 problems. Some companies (Meta in particular) expect two problems in 45 minutes, which means about 20 minutes per problem with no room for getting stuck.

## What Interviewers Evaluate

Beyond correctness, I found interviewers consistently assess:

Problem decomposition. Do you break the problem into steps before writing code? Candidates who jump straight into coding tend to produce messier solutions and miss edge cases.

Communication. Do you explain your approach before and during coding? Can you articulate tradeoffs between approaches? Interviewers want to understand your reasoning, not just your output.

Code quality. Clean variable names, consistent formatting, logical function structure. Code that looks like it could pass a code review scores higher than hacky solutions that produce the right output.

Testing instinct. Do you walk through your code with an example after writing it? Do you consider edge cases (empty input, single element, negative numbers, very large input) without being prompted?

Optimization awareness. Can you analyze the time and space complexity? Can you identify when your solution is suboptimal and suggest improvements?

## Pattern 1: Sliding Window

Use when: finding subarrays or substrings that meet a condition, optimizing over contiguous elements.

Template: maintain a window with two pointers (start and end). Expand the end pointer to include elements. Shrink the start pointer when the window violates a constraint.

Example problems:
- Maximum sum subarray of size k (fixed window)
- Longest substring with at most k distinct characters (variable window)
- Minimum window substring containing all characters of a pattern
- Fruits into baskets (longest subarray with at most 2 distinct values)
- Permutation in string (fixed window with frequency match)

Key insight: fixed-size windows are straightforward. Variable-size windows require a condition to trigger shrinking. Time complexity is usually O(n) because each element is visited at most twice.

## Pattern 2: Two Pointers

Use when: searching pairs in a sorted array, comparing elements from both ends, partitioning.

Template: place one pointer at the start and one at the end (or two pointers at the start moving at different speeds). Move pointers based on comparison with target.

Example problems:
- Two Sum II (sorted input)
- Three Sum (sort + two pointers for inner pair)
- Container With Most Water
- Remove duplicates from sorted array (in-place)
- Trapping Rain Water (two pointer approach)

Key insight: sorting the input first often enables two-pointer solutions. The technique reduces O(n^2) brute force to O(n) or O(n log n).

## Pattern 3: Fast and Slow Pointers

Use when: detecting cycles, finding middle elements, or determining properties of linked lists.

Template: one pointer moves one step at a time, the other moves two steps. They meet if a cycle exists. The slow pointer is at the middle when fast reaches the end.

Example problems:
- Linked list cycle detection
- Find the start of a linked list cycle
- Find the middle of a linked list
- Palindrome linked list (find middle, reverse second half, compare)
- Happy number (cycle detection in the digit sum sequence)

Key insight: this pattern uses O(1) space instead of O(n) for a hash set. Floyd's algorithm is the foundation.

## Pattern 4: Merge Intervals

Use when: dealing with overlapping intervals, scheduling, or time range problems.

Template: sort intervals by start time. Iterate and merge when current interval overlaps with the previous one.

Example problems:
- Merge overlapping intervals
- Insert interval into a sorted list
- Non-overlapping intervals (minimum removals)
- Meeting rooms (can attend all meetings?)
- Meeting rooms II (minimum conference rooms needed)
- Employee free time (common free time across schedules)

Key insight: always sort first. The merge logic is simple once sorted. For "minimum rooms" type problems, consider a sweep line or min-heap approach.

## Pattern 5: Cyclic Sort

Use when: problems involving arrays containing numbers in a given range (1 to n or 0 to n).

Template: iterate through the array. For each element, swap it to its correct index. After sorting, elements not at their correct index reveal the answer.

Example problems:
- Find the missing number (0 to n, one missing)
- Find all missing numbers
- Find the duplicate number
- Find all duplicates
- Find the first missing positive

Key insight: achieves O(n) time and O(1) space for problems that would otherwise need sorting or hash sets.

## Pattern 6: In-Place Reversal of Linked List

Use when: reversing a linked list or a portion of it.

Template: use three pointers (previous, current, next). At each step, reverse the current node's pointer, then advance all three.

Example problems:
- Reverse entire linked list
- Reverse a sublist (from position m to n)
- Reverse every k-group
- Reverse alternating k-group
- Rotate list by k positions

Key insight: draw the pointer manipulation on paper before coding. Off-by-one errors are the most common bug.

## Pattern 7: Tree BFS and DFS

Use when: traversing trees level by level (BFS) or exploring paths (DFS).

BFS template: use a queue. Process all nodes at current level before moving to the next.
DFS template: use recursion or an explicit stack. Explore one branch fully before backtracking.

Example problems:
- Level order traversal, zigzag traversal, right side view (BFS)
- Maximum depth, path sum, diameter of binary tree (DFS)
- Invert binary tree, symmetric tree
- Construct binary tree from preorder and inorder traversal
- Binary tree maximum path sum

Key insight: BFS for level-related questions, DFS for path-related questions. Most tree problems can be solved with either, but one is usually cleaner.

## Pattern 8: Two Heaps

Use when: finding the median in a stream, or problems requiring access to both the largest small element and the smallest large element.

Template: maintain a max-heap for the smaller half and a min-heap for the larger half. Balance their sizes so they differ by at most one.

Example problems:
- Find median from data stream
- Sliding window median
- IPO (maximize capital by selecting k projects)
- Next interval

Key insight: the median is always at the top of one or both heaps. Insertion is O(log n), median retrieval is O(1).

## Pattern 9: Subsets and Backtracking

Use when: generating combinations, permutations, or exploring all possible configurations.

Template: build the solution incrementally. At each step, make a choice, recurse, then undo the choice (backtrack).

Example problems:
- Generate all subsets (power set)
- Generate all permutations
- Combination sum (with and without repetition)
- Palindrome partitioning
- Generate parentheses
- Sudoku solver

Key insight: the time complexity is usually exponential (2^n for subsets, n! for permutations). Pruning invalid branches early is critical for performance.

## Pattern 10: Top K Elements

Use when: finding the k largest, smallest, or most frequent elements.

Template: use a heap of size k. For k largest, use a min-heap (the top is the smallest of the k largest). For k smallest, use a max-heap.

Example problems:
- Kth largest element in an array
- Top k frequent elements
- K closest points to origin
- Sort characters by frequency
- Kth smallest element in a sorted matrix

Key insight: heap approach gives O(n log k) which beats O(n log n) sorting when k is much smaller than n. Quick select gives O(n) average but O(n^2) worst case.

## Pattern 11: K-Way Merge

Use when: merging k sorted arrays, lists, or streams.

Template: use a min-heap containing one element from each list. Extract the minimum, add the next element from that list.

Example problems:
- Merge k sorted lists
- Kth smallest element in m sorted arrays
- Smallest range covering elements from k lists
- Find k pairs with smallest sums

Key insight: time complexity is O(n log k) where n is total elements and k is the number of lists. The heap size stays at k.

## Pattern 12: Topological Sort

Use when: ordering tasks with dependencies, detecting cycles in directed graphs.

Template: compute in-degrees. Start with nodes that have zero in-degree. Process them, reduce neighbors' in-degrees, add new zero-in-degree nodes.

Example problems:
- Course schedule (can finish all courses?)
- Course schedule II (find valid ordering)
- Alien dictionary (derive character ordering)
- Minimum height trees
- Sequence reconstruction

Key insight: if the topological sort includes all nodes, no cycle exists. If fewer nodes are processed, a cycle is present.

## Pattern 13: Union Find

Use when: grouping elements, detecting connected components, or determining if adding an edge creates a cycle.

Template: maintain a parent array and a rank array. Implement find with path compression and union by rank.

Example problems:
- Number of connected components
- Redundant connection (find the edge that creates a cycle)
- Accounts merge
- Longest consecutive sequence (alternative approach)
- Graph valid tree

Key insight: with path compression and union by rank, operations are nearly O(1) amortized. This beats BFS/DFS when you need dynamic connectivity.

## Pattern 14: Monotonic Stack

Use when: finding the next greater or smaller element, problems involving histogram-like comparisons.

Template: maintain a stack where elements are in increasing (or decreasing) order. Pop elements that violate the ordering when a new element arrives.

Example problems:
- Next greater element
- Daily temperatures
- Largest rectangle in histogram
- Trapping rain water (stack approach)
- Remove k digits to make smallest number

Key insight: each element is pushed and popped at most once, giving O(n) total time. The stack captures "waiting for resolution" elements.

## How to Prepare

Start by learning one pattern per day. For each pattern, solve 3-5 problems of increasing difficulty. After covering all patterns, do mixed practice where you identify which pattern applies.

Common mistakes I found candidates making:
- Jumping to code before discussing approach (interviewers want to hear your thinking)
- Not handling edge cases (empty input, single element, all same values)
- Writing correct but unreadable code (poor naming, no structure)
- Forgetting to analyze complexity after solving
- Getting stuck on optimal solution when a brute force with optimization would pass
- Not asking clarifying questions (input size, value range, sorted or unsorted)

My recommended approach for the 45-minute format:
1. Read the problem carefully (2 min)
2. Ask clarifying questions (2 min)
3. Identify the pattern and discuss approach (5 min)
4. Code the solution (20 min)
5. Walk through with an example (5 min)
6. Discuss edge cases and complexity (5 min)
7. Optimize if time permits (5 min)
