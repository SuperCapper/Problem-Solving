# 1. Fundamentals of Problem Solving

## 1.1 What is a "problem"?

A problem = a gap between a current state and a desired state, bound by constraints.

In math/CS: posed as a well-defined question needing a systematic approach.

## 1.2 Types of real-world problems

Real-world problems fall into a few categories:

- **Optimization** — e.g., fastest route between two cities: weighs distance, traffic, time of day.

- **Decision** — e.g., is a number prime: check divisibility by smaller numbers.

- **Search** — e.g., find a book in a large library: organize and navigate the collection.

- **Design** — e.g., bridge design: meet load capacity, material strength, environmental impact.

- **Prediction** — e.g., forecast weather from historical patterns.

## 1.3 Data Structures: the building blocks

Data representation starts with a simple analogy: a blank piece of paper.

The paper is a canvas. A "piece" of data = any discrete unit of information.

Represent pieces as squares — sides parallel to the paper's dimensions.

Draw two identical squares. They can be:

- non-touching,

- partially touching,

- fully touching, or

- overlapping


<p align="center">
<img width="524" height="411" alt="image" src="https://github.com/user-attachments/assets/f047cbc3-61f0-4059-9ca6-57373430cb71" />
</p>


Drop overlapping — it fuses data, breaking the discrete-unit requirement.

---

Squares are identical in size: data units are equal in magnitude, uniform in type.

Squares must not touch — the paper fills with non-intersecting squares. But isolated data is meaningless. Add lines connecting squares.


<p align="center">
<img width="598" height="459" alt="image" src="https://github.com/user-attachments/assets/e26938e5-fed2-4222-b4f7-50e39729afc1" />
</p>


Squares + lines = a **graph**. Lets you navigate from one data point to another — data referencing data. Core to data organization and algorithm design.

---

Place squares adjacently → a sequence. Extend it: linearly, or bi-dimensionally into rows and columns.


<p align="center">
<img width="783" height="480" alt="image" src="https://github.com/user-attachments/assets/a221ca76-1ad2-479e-a805-d8cb8d53dc9d" />
</p>


Rows and columns = a **table** — an **array** or **matrix** in code. Basis for ordered, grid-based storage and fast retrieval.

---

Assigning identity to an area of paper = two steps:

- Draw a boundary

- Name/label it

Boundary = a region of infinitely many points. Name = a finite string of symbols, mapped to a natural number.


<p align="center">
<img width="516" height="180" alt="image" src="https://github.com/user-attachments/assets/e5e66c2f-8345-4421-813c-316c0a1ea0d3" />
</p>


Labelling unlocks random access memory. Humans point straight at a square. A computer is "blind" — it must search the whole paper, unless given coordinates.

Cartesian coordinates fix this: give x/y, the computer selects each axis and lands on the right slot directly. This is **random access** (RAM) — jump straight to data by coordinates, no scanning.


<p align="center">
<img width="746" height="575" alt="image" src="https://github.com/user-attachments/assets/42e90cea-7be7-475c-b7cc-ac95752abfb4" />
</p>

---

Data boils down to two structures:

- the interconnected nodes of graphs and

- the orderly rows and columns of tables.

Simple, but deep: these two frameworks underpin all data organization.

On paper or in silicon: all information navigates through these two structures — points linked by relationships, or sequences laid out in a grid.

## 1.4 Solving problems with the State Space formulation

Problem-solving = navigating a **state space**: a series of transitions between states, driven by choices.

### 1.4.1 State Space Representation 

"Space" = every possible configuration (state) a system can occupy, given its variables, boundaries, constraints.

Represented as a graph:


<p align="center">
<img width="551" height="550" alt="image" src="https://github.com/user-attachments/assets/6c7cef1f-6de3-4458-abbf-dc0059a5f339" />
</p>


- **Current State (Si)**: the solution's configuration right now — all info needed to describe its status.


<p align="center">
<img width="449" height="180" alt="image" src="https://github.com/user-attachments/assets/1b618ead-281e-4c0a-938c-66d0c4d8523e" />
</p>


- **Choices (Ci)**: actions available from Si that transition to other states:


<p align="center">
<img width="270" height="56" alt="image" src="https://github.com/user-attachments/assets/10a57eb6-201e-4041-805f-251d803341d1" />
</p>


- **Transition Function (T)**: applying choice cij to Si gives new state Sj:


<p align="center">
<img width="167" height="53" alt="image" src="https://github.com/user-attachments/assets/14d6537b-7f09-4009-b655-ec731c0aa4a7" />
</p>


- **Final State (Sf)**: many possible goal types exist.

---

A common goal: reach a final state (Sf) that satisfies the problem's conditions — considered solved. Go state to state, applying choices, until success criteria are met. (Other goal types: later section.)

- **Reaching the Final State**: check specific conditions, e.g.:

- **Goal achievement**: has the desired outcome been attained (e.g., all puzzle pieces in place).

- **Constraint satisfaction**: are all constraints met (e.g., items packed within weight limit).

- **Optimization criteria**: does the solution meet/exceed a threshold (e.g., shortest path found).

- **Termination conditions**: have stopping criteria been hit (e.g., max iterations reached).

Which conditions apply depends on the problem and the desired solution characteristics.

### 1.4.2 Universal Problem Structure

Every problem fits this state/choice/transition/goal structure, so general techniques apply across domains:

- **Greedy Algorithms**: at each state, pick the best-looking immediate option, hoping it leads to the optimal final state.

- **Exhaustive Search**: explore every state and transition to guarantee the optimal solution.

- **Divide and Conquer**: split into independent subproblems, solve each, combine results.

- **Dynamic Programming**: reuse previously computed subproblem solutions to build the current state's solution. Maze pathfinding maps directly onto this framework (initial position → moves → new position → goal position).

### Example: Pathfinding in a Maze

Applying this to a maze:

- Initial State (So): starting position.

- Choices (Ci): possible moves (up, down, left, right).

- Transition Function (T): a move → a new position.

- Final State (S): the goal position.


<p align="center">
<img width="553" height="565" alt="image" src="https://github.com/user-attachments/assets/23dfdc78-7b94-41f1-a805-404ca809ea9d" />
</p>


The solution: a series of choices transitioning from initial state to final state through the maze's state space.

### 1.4.3 Summary 

Visualizing problems as state-space navigation gives a consistent, structured approach: every problem reduces to a sequence of state transitions, driven by choices, until the final state is reached.

## 1.5 Navigating Through State Space as Graph Traversal

Navigating a state space is graph traversal — this lets us reuse the rich toolset of graph theory to solve problems.

### 1.5.1 Exploring the Graph

State space as a graph → apply graph traversal techniques directly.

Non-exhaustive list:

- Breadth-First Search (BFS)

- Depth-First Search (DFS)

- Dijkstra's Algorithm

- A* Algorithm (not covered) 

### 1.5.2 Advantages of Graph Traversal for State Space Navigation

- **Clarity and Structure**: graphs give a clear, structured way to visualize and solve problems.

- **Algorithmic Tools**: a wide range of established graph-traversal/pathfinding algorithms apply directly.

- **Optimization**: graph methods find the shortest or least-costly path.

- **Scalability**: graph algorithms handle large, complex state spaces efficiently.

### 1.5.3 Summary 

State-space-as-graph-traversal is a powerful, versatile framework: states as **nodes**, transitions as **edges**. It leverages the full body of graph-theory knowledge — clarity, structure, efficiency.

## 1.6 The structure of problem decomposition

Complex problems break into subproblems: a **Directed Acyclic Graph (DAG)**, visualizing how components relate.


<p align="center">
<img width="585" height="476" alt="image" src="https://github.com/user-attachments/assets/fdb1ecdd-83cd-4b79-bc49-db059d0aab6f" />
</p>

In the DAG above:

- Nodes = subproblems or components.

- Edges = dependencies or relationships between components.

- Acyclic = no circular dependencies.

- Edge direction = flow of information / solving sequence.

---

The DAG gives a clear visual of a problem's structure, dependencies, and potential solution paths.

This lets us:

- Break complex problems into manageable parts

- Understand the order parts need addressing

- Identify independent subproblems solvable in parallel

- Recognize shared subproblems to avoid redundant work

### 1.6.1 Conditions for Collapse into a DAG 

A state-space/problem graph "collapses" into a DAG under certain conditions — usually a simplification enabling more efficient solutions.

- **Acyclic Nature**: no cycles or loops. Each node visited once; the graph flows one direction, no revisits.

- **Dependency Structure**: subproblems have strictly hierarchical dependencies — no circular dependencies.

### 1.6.2 Implications of Collapsing into a DAG

Collapsing into a DAG provides:

- **Subproblem Definition**: the problem decomposes into smaller, manageable subproblems — each node/state is one.

- **Topological Ordering**: strict hierarchy (no circular deps) lets the DAG be "topologically sorted" — an order that respects dependencies, solving each subproblem before it's needed elsewhere.

- **Efficiency in Problem-Solving**: acyclic → dynamic programming/memoization apply. Store subproblem results, reuse them, skip redundant computation.

### 1.6.3 Equivalence of DAG Collapse and Subproblem Decomposition 

Collapsing a graph into a DAG = recognizing the problem decomposes into subproblems. Why:

- **Hierarchical Subproblems**: a DAG is inherently a hierarchy — each node depends on its predecessors' results, same as building up from smaller problems to the larger solution.

- **No Cycles**: no cycles = a definite direction to problem-solving, like subproblems solved sequentially without looping back.

- **Reusability of Solutions**: once solved, a subproblem's solution is reusable by any dependent subproblem — the core of dynamic programming.

### 1.6.4 Example: Dynamic Programming

Classic case: Fibonacci, each number the sum of the two before it:


<p align="center">
<img width="301" height="43" alt="image" src="https://github.com/user-attachments/assets/d5abe114-ae51-4c39-996c-57ae0e7a93a8" />
</p>


- **Graph Representation**: each node = a Fibonacci number; edges = dependency (`Fn` depends on `Fn-1` and `Fn-2`).

- **DAG Structure**: looks like a tree, but it's a DAG — overlapping (repeated) subproblems, no cycles. Once computed, a number is reused by later numbers without revisiting.

- **Subproblem Decomposition**: each Fibonacci number depends on two smaller subproblems. DP computes each efficiently by storing and reusing prior values.


<p align="center">
<img width="796" height="375" alt="image" src="https://github.com/user-attachments/assets/98d61eb0-dcc3-41de-b9c3-61560b7d315d" />
</p>


### 1.6.5 Summary

A graph collapses into a DAG when it structures into a hierarchy of subproblems with no cyclic dependencies — meaning the problem decomposes into manageable pieces, enabling techniques like dynamic programming.

The DAG gives a clear solve order: each subproblem's solution is ready when a dependent subproblem needs it. Graph theory and algorithm design synergize here.

The Fibonacci sequence illustrates this: it looks like a tree of recursive calls, but is really a DAG with overlapping subproblems (`Fn` depends on `Fn-1` and `Fn-2`), which is exactly why memoizing previously computed values makes it efficient.

## 1.7 What is a solution?

A solution bridges current and desired state, respecting constraints. In computational problems, it typically has these traits:

- **Correctness**: accurately addresses the problem per its requirements.

- **Efficiency**: saves time and resources — practical for real-world use.

- **Completeness**: works for all valid inputs — reliable.

- **Clarity**: easy to understand, implement, maintain.

- **Robustness**: handles unexpected inputs gracefully, no failures.

- **Scalability**: performs well as problem size grows.

Multiple valid solutions often trade these traits off differently; the best choice depends on context. Knowing what a solution is guides algorithm design and evaluation.

### 1.7.1 Types of Solutions in State Space 

Within the state-space framework, a "solution" can take several forms:


#### **Single Final State (S'f')** — one specific goal state (e.g., the maze exit)

- **Definition**: a single, specific state signifying completion.

- **Example**: reaching the exit cell (S'f') in a maze.

- **Graph Representation**: a path from initial state (S'o') to this final state (S'f').


<p align="center">
<img width="443" height="295" alt="image" src="https://github.com/user-attachments/assets/dac36fd3-8308-401d-8f9a-ea1560f264b9" />
</p>


#### **Set of Final States (F)** — any of several acceptable end states (e.g., any winning score in a game)

- **Definition**: a collection of acceptable final states — any one is a valid solution.

- **Example**: any of several winning states in a game. Football: states as (goals A, goals B) — winning states include (1,0), (2,0), (2,1), (3,2)…

- **Graph Representation**: multiple paths from (S'o') to any state in set F.


<p align="center">
<img width="445" height="291" alt="image" src="https://github.com/user-attachments/assets/c2546e87-70bf-4df4-a630-e3d65a000145" />
</p>


#### **Sequence of states** — the ordered path of steps taken (e.g., moves in a puzzle)

- **Definition**: the ordered sequence of states/steps taken to reach the solution.

- **Example**: the move sequence in a puzzle, start to completion.

- **Graph Representation**: the specific sequence of nodes and edges from (S'o') to (S'f').


<p align="center">
<img width="638" height="222" alt="image" src="https://github.com/user-attachments/assets/225e3468-8726-43b5-becc-193d7bb7d6f8" />
</p>


#### **Optimal path** — the most efficient path by some metric (e.g., shortest route)

- **Definition**: the path reaching the final state most efficiently by a given metric (shortest, least cost).

- **Example**: shortest route in a travel itinerary.

- **Graph Representation**: minimal edges or least cumulative weight from (S'o') to (S'f').


<p align="center">
<img width="557" height="350" alt="image" src="https://github.com/user-attachments/assets/bc31ff06-a540-4627-895a-f628e0733292" />
</p>


#### **All possible paths** — every path from start to goal(s) (e.g., enumerating combinations)

- **Definition**: every possible path from initial to final state(s) — the complete solution set.

- **Example**: generating all combinations satisfying a condition.

- **Graph Representation**: the solution set = all paths from (S'o') to the final states.


<p align="center">
<img width="825" height="622" alt="image" src="https://github.com/user-attachments/assets/3455b2f0-7971-4996-9150-23e9922c720e" />
</p>


Above example (3 = start, 9 = final): solution paths are:


<p align="center">
<img width="348" height="42" alt="image" src="https://github.com/user-attachments/assets/d04087b9-6bad-4434-b14d-640da569d09a" />
</p>


---

#### **State space coverage** — visiting all reachable states (e.g., exhaustive search)

- **Definition**: covering all reachable states from the initial state — nothing missed.

- **Example**: exhaustive search over the entire state space.

- **Graph Representation**: traversing the whole graph, or a significant portion.


<p align="center">
<img width="609" height="395" alt="image" src="https://github.com/user-attachments/assets/77babb02-c6df-4666-9bd3-7dc49be13b24" />
</p>


### 1.7.2 Determining the Type of Solution Needed

Depends on context and goals:

- **Optimization Problems**: usually need an optimal path (shortest, least cost).

- **Search Problems**: need a single final state or a set of final states.

- **Exploratory Problems**: may need all possible paths or full state-space coverage.

#### Example: Travelling Salesperson Problem (TSP)

- **Single Final State**: a route visiting all cities and returning to start — the completed tour.

- **Optimal Path**: the shortest route visiting all cities.

- **Sequence of States**: the order of cities visited on the optimal route.

#### Example: Sudoku Puzzle

- **Single Final State**: a filled, valid Sudoku grid.

- **Sequence of States**: the moves made from initial to final grid.

- **All Possible Paths**: every move sequence that completes the grid.

Note: even a "continuous" state space reduces to a discrete state-space graph once every change is treated as a discrete step.

### 1.8 Conclusion

This chapter covered problem definitions and types, then the foundational elements of data structures — core concepts for a systematic, efficient approach to problem-solving.

We introduced state space as a graph, framed navigating it as graph traversal (unlocking graph-based algorithms), and showed how complex problems decompose into subproblems via Directed Acyclic Graphs (DAGs) — enabling dynamic programming and similar techniques.

---

This chapter set the vocabulary for everything that follows: problem types, the two core data structures (graphs, tables), the state-space formulation (state, choices, transitions, final state), state-space navigation as graph traversal, DAG decomposition, and the forms a "solution" can take. Everything in later chapters builds on this.

Core concepts for approaching problems before writing any code: understanding requirements, breaking problems into smaller pieces, and choosing a strategy (brute force, greedy, divide and conquer, dynamic programming, etc.).

Contents:

- Problem decomposition

- Pattern recognition

- Choosing an approach

- Common problem-solving heuristics
