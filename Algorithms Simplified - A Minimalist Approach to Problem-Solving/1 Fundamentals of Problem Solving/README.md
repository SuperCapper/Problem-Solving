# 1. Fundamentals of Problem Solving

Summary of Chapter 1 from *Algorithms Simplified: A Minimalist Approach to Problem-Solving* (Rohith B V).

## 1.1 What is a "problem"?

A problem is a gap between a current state and a desired state, bound by a set of constraints. In math and computer science, it's usually posed as a well-defined question that demands a systematic approach to solve.

## 1.2 Types of real-world problems

Real-world problems generally fall into a few categories:
- **Optimization** — e.g., finding the fastest route between two cities.
- **Decision** — e.g., determining whether a number is prime.
- **Search** — e.g., finding a specific book in a large library.
- **Design** — e.g., designing a bridge that meets load and material constraints.
- **Prediction** — e.g., forecasting weather from historical patterns.

## 1.3 Data Structures: the building blocks

Using a "squares on paper" analogy, data pieces (squares) can be non-touching, partially touching, fully touching, or overlapping — overlapping is excluded since it would fuse distinct data units. Connecting squares with lines produces a **graph**, letting data reference other data. Arranging squares adjacently in rows and columns produces a **table/array/matrix**. Giving a square a boundary and a label enables **random access**: a computer can jump directly to a piece of data via its coordinates rather than scanning everything.

The key takeaway: nearly all data organization reduces to two fundamental structures — **graphs** (interconnected nodes) and **tables** (ordered rows and columns).

## 1.4 Solving problems with the State Space formulation

Problem-solving can be modeled as navigating a **state space**, where a solution is a series of transitions between states driven by choices.

- **State (Si)** — a configuration `(v1, v2, ..., vn)` describing the system at a point in time.
- **Choices (Ci)** — the set of actions available from a given state.
- **Transition Function (T)** — `T(Si, cij) = Sj`, applying a choice to move from one state to another.
- **Final State (Sf)** — a state satisfying the problem's success criteria (goal achievement, constraint satisfaction, optimization threshold, or termination condition).

Because every problem can be cast into this state/choice/transition/goal structure, general techniques apply across domains:
- **Greedy algorithms** — pick the best-looking immediate choice at each step.
- **Exhaustive search** — explore all states/transitions to guarantee optimality.
- **Divide and conquer** — split into independent subproblems and combine results.
- **Dynamic programming** — reuse previously computed subproblem solutions.

Example: maze pathfinding maps directly onto this framework (initial position → moves → new position → goal position).

## 1.5 Navigating Through State Space as Graph Traversal

Since state spaces are graphs, standard graph traversal algorithms apply directly: **BFS**, **DFS**, **Dijkstra's algorithm**, and **A\*** (covered later). Framing state-space navigation as graph traversal gives four advantages: clarity/structure, a large library of existing algorithmic tools, built-in optimization (shortest/least-cost paths), and scalability to large state spaces.

## 1.6 The structure of problem decomposition

Complex problems can be broken into subproblems represented as a **Directed Acyclic Graph (DAG)**, where nodes are subproblems and edges are dependencies between them.

A state-space graph "collapses" into a DAG when:
- It is **acyclic** (no node is revisited).
- Its subproblems have a **strictly hierarchical dependency structure** (no circular dependencies).

When this collapse happens, it unlocks:
- **Topological ordering** — a valid sequence for solving subproblems.
- **Efficiency gains** — dynamic programming and memoization become applicable, since acyclic subproblem results can be cached and reused.

The Fibonacci sequence illustrates this: it looks like a tree of recursive calls, but is really a DAG with overlapping subproblems (`Fn` depends on `Fn-1` and `Fn-2`), which is exactly why memoizing previously computed values makes it efficient.

## 1.7 What is a solution?

A solution bridges the current and desired state while respecting constraints. Good solutions tend to be **correct**, **efficient**, **complete**, **clear**, **robust**, and **scalable** — though multiple valid solutions may trade these qualities off differently.

Within the state-space framework, a "solution" can take several forms:
- **Single final state** — one specific goal state (e.g., the maze exit).
- **Set of final states** — any of several acceptable end states (e.g., any winning score in a game).
- **Sequence of states** — the ordered path of steps taken (e.g., moves in a puzzle).
- **Optimal path** — the most efficient path by some metric (e.g., shortest route).
- **All possible paths** — every path from start to goal(s) (e.g., enumerating combinations).
- **State space coverage** — visiting all reachable states (e.g., exhaustive search).

Which type of solution is appropriate depends on context: optimization problems usually want an optimal path, search problems want a single or set of final states, and exploratory problems may need all paths or full coverage. The Travelling Salesperson Problem and Sudoku are worked examples showing how a single problem can be viewed through multiple solution-type lenses at once. Even continuous state spaces reduce to discrete state-space graphs once every change is treated as a discrete step.

## 1.8 Conclusion

This chapter established the vocabulary for everything that follows: problems and their types, the two foundational data structures (graphs and tables), the state-space formulation (state, choices, transitions, final state), state-space navigation as graph traversal, problem decomposition via DAGs, and the different forms a "solution" can take. These concepts underpin the algorithms and techniques covered in later chapters.
