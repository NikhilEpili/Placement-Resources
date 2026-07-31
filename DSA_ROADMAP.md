# 90-Day DSA Roadmap — From "I Know the Theory" to "I Can Solve New Problems"

## Why you're stuck (and how this plan fixes it)

Knowing that DP exists and knowing *when to use it on a problem you've never seen* are two different skills. The gap closes through:

1. **Pattern-based practice**, not topic-based — you solve problems grouped by the *technique* they test, so your brain builds a lookup table: "sorted array + target → two pointers," "substring + constraint → sliding window."
2. **Struggling before looking at solutions** — timeboxed attempts force you to generate ideas, which is the actual skill interviews test.
3. **Reflection after every problem** — write one line: *what was the trigger that should've told me the pattern?* This is the single highest-leverage habit in this whole plan.
4. **Re-solving problems later** (spaced repetition) — recognition sticks only after the 2nd or 3rd exposure.

---

## The method for every single problem (use this every time)

1. **Read + restate** the problem in your own words (1 min).
2. **Identify signals** — array sorted? need pairs/triplets? substring/subarray? tree/graph? "count ways" or "min/max" → probably DP? (1–2 min)
3. **Timebox an attempt**: Easy 15 min / Medium 25 min / Hard 35 min. Write pseudocode or brute force even if you can't optimize.
4. **If stuck after timebox** → look at just the *hint/approach name* (not full solution) and try again for 10 more minutes.
5. **Only then** read the full solution. Code it yourself from scratch, don't copy-paste.
6. **Log it** (see tracker below): pattern name, the trigger signal you missed, one sentence on why the approach works.
7. **Re-attempt cold** after 7 days and 21 days for anything you couldn't solve independently.

Keep a simple tracker (sheet or notes app) with columns: `Date | Problem | Pattern | Solved Independently? (Y/N) | Trigger I missed | Revisit Date`.

---

## Core resources (don't scatter across 10 sources — pick these)

- **Primary problem list:** [NeetCode 150](https://neetcode.io/practice) (also has free video explanations for every problem — use videos only after your timeboxed attempt)
- **Pattern reference:** *Grokking the Coding Interview* (patterns like "Sliding Window," "Merge Intervals," "Two Pointers" — great for building the trigger→pattern map)
- **Indian-audience alternative/supplement:** [Striver's SDE Sheet / A2Z DSA Course](https://takeuforward.org/strivers-a2z-dsa-course/strivers-a2z-dsa-course-sheet-2/) — excellent, free, well-sequenced
- **For deep dives on tricky topics:** NeetCode YouTube channel, Abdul Bari (algorithms fundamentals)
- **Mock contests (weeks 11–13):** LeetCode weekly/biweekly contests — do these live, don't just read editorials afterward

---

## Structure: 13 weeks × 7 days, 5 problems/day (~450 problems total)

Each week = one pattern family. Days 1–4 build the pattern with Easy→Medium; Days 5–6 push into Medium→Hard; Day 7 is **mixed review** (older patterns) + write your reflection log for the week.

### Week 1 (Days 1–7): Arrays & Hashing
- D1: Two Sum · Contains Duplicate · Valid Anagram · Best Time to Buy/Sell Stock · Concatenation of Array
- D2: Product of Array Except Self · Majority Element · Move Zeroes · Single Number · Missing Number
- D3: Group Anagrams · Top K Frequent Elements · Encode and Decode Strings · Longest Consecutive Sequence · Two Sum II
- D4: Valid Sudoku · Subarray Sum Equals K · Contiguous Array · Set Matrix Zeroes · Rotate Array
- D5: 3Sum · 4Sum · Sort Colors · Next Permutation · Merge Intervals
- D6: Insert Interval · Non-overlapping Intervals · First Missing Positive · Spiral Matrix · Rotate Image
- D7 (Review): Pick 5 from D1–D6 you struggled with, re-solve cold + log reflections

### Week 2 (Days 8–14): Two Pointers & Sliding Window
- D8: Valid Palindrome · Two Sum II · Container With Most Water · Trapping Rain Water (attempt) · Remove Duplicates from Sorted Array
- D9: Best Time to Buy/Sell Stock II · 3Sum Closest · Sort Array by Parity · Squares of a Sorted Array · Backspace String Compare
- D10: Longest Substring Without Repeating Characters · Minimum Size Subarray Sum · Max Consecutive Ones III · Fruit Into Baskets · Longest Repeating Character Replacement
- D11: Permutation in String · Find All Anagrams in a String · Minimum Window Substring · Sliding Window Maximum · Longest Substring with At Most K Distinct Characters
- D12: Subarray Product Less Than K · Max Sum Subarray of Size K · Count Number of Nice Subarrays · Binary Subarrays With Sum · Grumpy Bookstore Owner
- D13: Trapping Rain Water (solve fully) · Boats to Save People · Partition Labels · Dutch National Flag · Two Sum (sorted variant, no extra space)
- D14 (Review): Mixed re-solve + reflection log

### Week 3 (Days 15–21): Stack & Queues
- D15: Valid Parentheses · Min Stack · Implement Queue using Stacks · Baseball Game · Next Greater Element I
- D16: Daily Temperatures · Next Greater Element II · Evaluate Reverse Polish Notation · Remove All Adjacent Duplicates in String · Backspace Compare (stack approach)
- D17: Generate Parentheses · Decode String · Asteroid Collision · Simplify Path · Remove K Digits
- D18: Largest Rectangle in Histogram · Trapping Rain Water (stack approach) · Basic Calculator II · Online Stock Span · Car Fleet
- D19: Sliding Window Maximum (deque approach) · Design Circular Queue · 132 Pattern · Remove Duplicate Letters · Score of Parentheses
- D20: Implement Stack using Queues · Exclusive Time of Functions · Maximum Frequency Stack · Minimum Remove to Make Valid Parentheses · Flatten Nested List Iterator
- D21 (Review): Mixed re-solve + reflection log

### Week 4 (Days 22–28): Binary Search
- D22: Binary Search (basic) · Search Insert Position · First and Last Position in Sorted Array · Search in Rotated Sorted Array · Find Minimum in Rotated Sorted Array
- D23: Search a 2D Matrix · Search a 2D Matrix II · Find Peak Element · Sqrt(x) · Guess Number Higher or Lower
- D24: Koko Eating Bananas · Capacity To Ship Packages Within D Days · Split Array Largest Sum · Time Based Key-Value Store · Median of Two Sorted Arrays (attempt)
- D25: Find K Closest Elements · Search in Rotated Sorted Array II · Single Element in a Sorted Array · H-Index II · Peak Index in a Mountain Array
- D26: Kth Smallest Element in a Sorted Matrix · Median of Two Sorted Arrays (solve fully) · Aggressive Cows (GfG/Codeforces style) · Minimize Max Distance to Gas Station · Random Pick with Weight
- D27: Find the Duplicate Number (binary search approach) · Book Allocation Problem · Painter's Partition Problem · Count of Smaller Numbers After Self (BS variant) · Search a 2D Matrix (variant with rotation)
- D28 (Review): Mixed re-solve + reflection log

### Week 5 (Days 29–35): Linked List
- D29: Reverse Linked List · Merge Two Sorted Lists · Linked List Cycle · Middle of the Linked List · Remove Duplicates from Sorted List
- D30: Remove Nth Node From End of List · Reorder List · Palindrome Linked List · Intersection of Two Linked Lists · Add Two Numbers
- D31: Copy List with Random Pointer · LRU Cache · Odd Even Linked List · Swap Nodes in Pairs · Rotate List
- D32: Reverse Linked List II · Reverse Nodes in k-Group · Flatten a Multilevel Doubly Linked List · Sort List · Partition List
- D33: Merge K Sorted Lists · LFU Cache · Design Linked List · Delete Node in a Linked List · Convert Binary Number in Linked List to Integer
- D34: Linked List Cycle II · Split Linked List in Parts · Insertion Sort List · Remove Duplicates from Sorted List II · Plus One Linked List
- D35 (Review): Mixed re-solve + reflection log

### Week 6 (Days 36–42): Trees (Binary Tree / BST)
- D36: Invert Binary Tree · Maximum Depth of Binary Tree · Diameter of Binary Tree · Balanced Binary Tree · Same Tree
- D37: Subtree of Another Tree · Lowest Common Ancestor of BST · Binary Tree Level Order Traversal · Binary Tree Right Side View · Count Good Nodes in Binary Tree
- D38: Validate Binary Search Tree · Kth Smallest Element in a BST · Construct Binary Tree from Preorder and Inorder · Binary Tree Maximum Path Sum · Serialize and Deserialize Binary Tree
- D39: Lowest Common Ancestor of Binary Tree · Path Sum II · Flatten Binary Tree to Linked List · Populating Next Right Pointers · Sum Root to Leaf Numbers
- D40: Binary Tree Zigzag Level Order Traversal · Vertical Order Traversal of a Binary Tree · Convert Sorted Array to BST · Delete Node in a BST · Insert into a BST
- D41: Recover Binary Search Tree · Binary Tree Boundary Traversal · Maximum Width of Binary Tree · House Robber III · All Nodes Distance K in Binary Tree
- D42 (Review): Mixed re-solve + reflection log

### Week 7 (Days 43–49): Tries, Heaps & Priority Queue
- D43 (Trie): Implement Trie · Design Add and Search Words Data Structure · Word Search II · Replace Words · Longest Word in Dictionary
- D44 (Heap): Kth Largest Element in an Array · Last Stone Weight · K Closest Points to Origin · Kth Largest Element in a Stream · Top K Frequent Elements (heap approach)
- D45 (Heap): Task Scheduler · Design Twitter · Single-Threaded CPU · Reorganize String · Furthest Building You Can Reach
- D46 (Heap): Find Median from Data Stream · Meeting Rooms II · IPO · Minimum Cost to Connect Sticks · Sliding Window Median
- D47 (Mixed): Ugly Number II · Super Ugly Number · K Closest Points (variant) · Smallest Range Covering Elements from K Lists · Employee Free Time
- D48 (Mixed): Merge K Sorted Lists (heap approach) · Rearrange String k Distance Apart · Maximum Performance of a Team · CPU Task Scheduling variant · Trapping Rain Water II
- D49 (Review): Mixed re-solve + reflection log

### Week 8 (Days 50–56): Backtracking
- D50: Subsets · Subsets II · Combination Sum · Combination Sum II · Permutations
- D51: Permutations II · Word Search · Palindrome Partitioning · Letter Combinations of a Phone Number · Generate Parentheses (revisit as backtracking)
- D52: N-Queens · N-Queens II · Sudoku Solver · Restore IP Addresses · Combination Sum III
- D53: Word Break II · Beautiful Arrangement · Matchsticks to Square · Partition to K Equal Sum Subsets · Split a String Into the Max Number of Unique Substrings
- D54: Expression Add Operators · Gray Code · Additive Number · Find Unique Binary String · Path with Maximum Gold
- D55: The Knight's Tour (variant) · Word Ladder II (as backtracking + BFS) · Palindrome Partitioning II · Unique Paths III · Android Unlock Patterns
- D56 (Review): Mixed re-solve + reflection log

### Week 9 (Days 57–63): Graphs — BFS/DFS Foundations
- D57: Number of Islands · Max Area of Island · Flood Fill · Clone Graph · Islands and Treasure (Walls and Gates)
- D58: Rotting Oranges · Course Schedule · Course Schedule II · Pacific Atlantic Water Flow · Surrounded Regions
- D59: Graph Valid Tree · Number of Connected Components in an Undirected Graph · Word Ladder · Redundant Connection · Is Graph Bipartite?
- D60: Keys and Rooms · All Paths From Source to Target · Employee Importance · As Far from Land as Possible · 01 Matrix
- D61: Shortest Path in Binary Matrix · Time Needed to Inform All Employees · Minimum Height Trees · Reconstruct Itinerary · Evaluate Division
- D62: Snake and Ladders · Open the Lock · Bus Routes · Cheapest Flights Within K Stops (BFS attempt) · Shortest Bridge
- D63 (Review): Mixed re-solve + reflection log

### Week 10 (Days 64–70): Advanced Graphs
- D64: Union-Find basics: Redundant Connection (DSU approach) · Number of Provinces · Accounts Merge · Most Stones Removed with Same Row or Column · Satisfiability of Equality Equations
- D65: Topological Sort: Alien Dictionary · Course Schedule (topo approach) · Sequence Reconstruction · Minimum Height Trees (topo approach) · Parallel Courses
- D66: Dijkstra: Network Delay Time · Cheapest Flights Within K Stops (Dijkstra/Bellman-Ford) · Path with Maximum Probability · Swim in Rising Water · Path with Minimum Effort
- D67: Bellman-Ford / Floyd-Warshall: Find the City With the Smallest Number of Neighbors · Cheapest Flights (Bellman-Ford) · Negative weight cycle detection practice · Find Eventual Safe States · Critical Connections in a Network (bridges)
- D68: MST: Min Cost to Connect All Points · Connecting Cities With Minimum Cost · Optimize Water Distribution in a Village · Find Critical and Pseudo-Critical Edges in MST · Number of Operations to Make Network Connected
- D69: Mixed advanced: Reconstruct Itinerary (Eulerian path) · Word Ladder II (full) · Bus Routes (revisit) · Regions Cut By Slashes (DSU) · Graph Connectivity with Threshold
- D70 (Review): Mixed re-solve + reflection log

### Week 11 (Days 71–77): 1D Dynamic Programming
- D71: Climbing Stairs · House Robber · House Robber II · Min Cost Climbing Stairs · Fibonacci Number (recursion → memo → tabulation, all 3 ways)
- D72: Longest Increasing Subsequence · Maximum Subarray · Maximum Product Subarray · Coin Change · Coin Change II
- D73: Word Break · Decode Ways · Partition Equal Subset Sum · Target Sum · Combination Sum IV
- D74: Longest Palindromic Substring · Palindromic Substrings · Perfect Squares · Integer Break · Jump Game
- D75: Jump Game II · Longest Common Subsequence · Delete Operation for Two Strings · Edit Distance · Distinct Subsequences
- D76: Interleaving String · Longest Palindromic Subsequence · Wildcard Matching · Regular Expression Matching · Minimum ASCII Delete Sum for Two Strings
- D77 (Review): Mixed re-solve + reflection log

### Week 12 (Days 78–84): 2D DP, Knapsack Variants & Greedy
- D78: Unique Paths · Unique Paths II · Minimum Path Sum · Triangle · Dungeon Game
- D79: 0/1 Knapsack (practice on GfG/Codeforces) · Partition Equal Subset Sum (revisit as knapsack) · Last Stone Weight II · Ones and Zeroes · Profitable Schemes
- D80: Best Time to Buy/Sell Stock III · Best Time to Buy/Sell Stock IV · Best Time to Buy/Sell Stock with Cooldown · Best Time to Buy/Sell Stock with Transaction Fee · Maximum Profit in Job Scheduling
- D81: Burst Balloons · Matrix Chain Multiplication (GfG) · Minimum Cost to Cut a Stick · Stone Game · Predict the Winner
- D82 (Greedy): Jump Game (revisit as greedy) · Gas Station · Candy · Non-overlapping Intervals (revisit) · Task Scheduler (revisit)
- D83 (Greedy): Partition Labels (revisit) · Minimum Number of Arrows to Burst Balloons · Queue Reconstruction by Height · Boats to Save People (revisit) · Greedy Florist / Assignment style problems
- D84 (Review): Mixed re-solve + reflection log

### Week 13 (Days 85–90): Consolidation & Mock Interviews
- D85: Take 1 full LeetCode weekly/biweekly contest, live, timed
- D86: Redo 5 problems you failed to solve independently in weeks 1–4 (cold, no notes)
- D87: Redo 5 problems you failed to solve independently in weeks 5–8 (cold, no notes)
- D88: Redo 5 problems you failed to solve independently in weeks 9–12 (cold, no notes)
- D89: Mixed random 5 (use LeetCode's random problem picker, medium difficulty, across all patterns) — simulate interview conditions, explain out loud as you code
- D90: Take another timed contest + write a reflection doc: which patterns are still weak, plan next 30 days

---

## Daily time budget (roughly 2–2.5 hrs/day)
- Warm-up (5 min): skim yesterday's reflection log
- 5 problems (90–120 min): timeboxed attempts per the method above
- Reflection log (10 min): fill tracker for today's problems
- Weekly (Day 7 of each week): 30 extra min to re-solve flagged problems cold

## Rules that make this actually work
- **Don't skip the struggle phase.** Watching a solution video before attempting feels productive but doesn't build the skill you're missing.
- **Say your approach out loud** (or type it as a comment) before coding — this mimics interview conditions and forces you to commit to a plan instead of coding by trial and error.
- **It's fine to not finish all 5 some days.** Depth on fewer problems (full struggle + solve + log) beats rushing through 5 with solutions open.
- **Revisit is not optional.** The 7-day/21-day cold re-attempts are where pattern recognition actually forms.
