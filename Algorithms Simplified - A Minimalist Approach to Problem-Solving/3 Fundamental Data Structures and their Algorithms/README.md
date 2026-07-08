# 3. Fundamental Data Structures and their Algorithms

Summary of Chapter 3 from *Algorithms Simplified: A Minimalist Approach to Problem-Solving* (Rohith B V).

## 3.1 Introduction

Graphs and tables are the two core structures underlying efficient problem-solving. Graphs model relationships and processes — social networks, road networks, computer networks. Tables (arrays and hash tables) enable fast data access and manipulation: arrays are ideal for indexed operations like sorting and binary search, while hash tables offer near-instant key-value lookups for caches, dictionaries, and routing tables.

## 3.2 Undirected Graphs

In an undirected graph, relationships are mutual (e.g., Facebook friendships) and represented as lines without arrows.

- **Depth-First Search (DFS)** — explore as far as possible down one path before backtracking, like navigating a maze. Good for path-existence checks. Real-world use: depth-limited DFS for game AI (e.g., looking ahead in chess).
- **Breadth-First Search (BFS)** — explore all neighboring nodes before moving further out, like torchlight spreading evenly. Real-world use: finding shortest connection chains in social networks ("six degrees of separation").
- **Trees** — hierarchical graphs with a root node branching into children (e.g., a family tree or org chart). Traversal orders:
  - **Pre-order** — node, then left subtree, then right subtree.
  - **In-order** — left subtree, node, right subtree; yields sorted order on a Binary Search Tree (BST).
  - **Post-order** — left subtree, right subtree, node; useful for deleting a tree bottom-up.
  - **Level-order** — visit level by level (equivalent to BFS from the root).
  - Real-world use: file systems are trees — post-order for total size, pre-order for displaying structure.

## 3.3 General Directed Graphs

Directed graphs have one-way relationships (e.g., Twitter follows) shown as arrows, and can contain cycles. They model web links, one-way roads, and workflows. The same traversal algorithms as undirected graphs apply, as long as edge direction is respected.

## 3.4 Directed Acyclic Graphs (DAGs)

A DAG is a directed graph with no cycles — e.g., a project schedule where tasks depend on prior tasks completing.

- **Topological sorting** — orders DAG nodes so all dependency edges point forward, giving a valid execution/completion order. Real-world use: build systems use topological sort to compile components in dependency order.

## 3.5 Linked Lists

Elements form a chain, each pointing to the next (and/or previous) node. Efficient for frequent insertion/removal at the ends. Real-world uses: undo functionality in text editors (each node = a document state), music playlists (each node = a song).

## 3.6 Weighted Graphs

Edges carry values (distance, cost, time, etc.), e.g., a road network weighted by travel time.

- **Dijkstra's Algorithm** — finds the shortest path between two nodes in a weighted graph (and, as a byproduct, the shortest path from the source to every other node). Real-world use: GPS/navigation systems like Google Maps.
- **Prim's Algorithm** — finds the minimum spanning tree (the subset of edges connecting all nodes with minimum total weight). Real-world use: designing efficient networks (e.g., minimizing cable length connecting all computers, or rail lines connecting cities).

## 3.7 Arrays

Arrays store elements in contiguous memory, giving O(1) index-based access — like a wall of numbered lockers. They underlie stacks (LIFO), queues (FIFO), heaps, and multi-dimensional tables.

- **Arrays and RAM** — an element's memory address is computed directly from its index (`base_address + index * element_size`), which is why access is O(1).
- **Arrays as complete graphs** — conceptually, every element is directly "connected" to every other element (an implicit edge between any pair), which is another way to see why arbitrary access/swaps are cheap.
- **Algorithms on arrays**:
  - **Quicksort** — divide-and-conquer: pick a pivot, partition into less-than/greater-than sub-arrays, recurse. Average O(n log n) time, O(log n) space, in-place, fast in practice but O(n²) worst case.
  - **Mergesort** — divide-and-conquer: split in half, sort each half, merge. Stable O(n log n) time, O(n) space; better worst-case guarantees than quicksort but needs more memory.
  - **Binary search** — repeatedly halve a *sorted* array to find a target. O(log n) time, O(1) space (iterative) or O(log n) (recursive). Requires sorted data and random access. Used for dataset lookup, database indexing, and as a building block for other algorithms.

## 3.8 Dictionaries

Dictionaries (associative arrays / hash maps / hash tables) store key-value pairs, implemented on top of arrays via hashing, enabling near-instant lookup and update.

- **Hashing** — transforms arbitrary input into a fixed-size hash value via a hash function (illustrated with a "potatoes → hash browns" analogy: irreversible, uniform, and fast). Common hash functions: MD5, SHA-1, SHA-256.
- **Password storage** — systems store a password's hash, not the plaintext; login compares the hash of the entered password to the stored hash (with real systems adding salting/peppering for extra security). Hashing is valuable here because it's irreversible, deterministic, and fast.
- **Hashing and array indexing** — an object's hash, taken modulo the array size, gives its index/bucket — cheap to compute (like RAM access) and spreads objects randomly enough to minimize collisions.

## 3.9 Sets

Sets are unordered collections of unique elements, typically implemented with hash tables — effectively a dictionary where the key equals the value.

- **Add / remove / membership check** — O(1) average case, O(n) worst case (hash and access the relevant bucket).
- **Union** — O(m + n): build a new set containing all elements of both sets.
- **Intersection** — O(min(m, n)): iterate the smaller set, check membership in the larger.
- **Difference** — O(m): build a new set of elements in the first set but not the second.

## 3.10 Conclusion

Graphs and their algorithms (DFS, BFS, Dijkstra's, Prim's, topological sort) provide a general framework for modeling and optimizing relationships and processes — from social networks and GPS navigation to project scheduling and networking. Tables — arrays, dictionaries, and sets — form the backbone of efficient data access, sorting, searching, and key-value/uniqueness management, largely thanks to O(1) indexed access and hashing. Together, these structures and their algorithms are the foundational toolkit for tackling complex problems across domains.
