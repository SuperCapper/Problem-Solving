# 1. Fundamentals of Problem Solving

## 1.1 What is a "problem"?

A problem, in its essence, is a situation that requires resolution. It is a gap between a current state and a desired state, bound by a set of constraints. 

In math and computer science, it's usually posed as a well-defined question that demands a systematic approach to solve.

## 1.2 Types of real-world problems

Real-world problems generally fall into a few categories:

- **Optimization** — e.g., finding the fastest route between two cities can involve considering various factors like distance, traffic and time of day.

- **Decision** — e.g., determining whether a number is prime involves checking divisibility by smaller numbers.

- **Search** — e.g., finding a specific book in a large library involves organizing and navigating the collection efficiently.

- **Design** — e.g., designing a bridge that meets load and material constraints requires meeting criteria such as load capacity, material strength and environmental impact.

- **Prediction** — e.g., forecasting weather from historical patterns involves analyzing patterns in historical data to forecast future conditions.

## 1.3 Data Structures: the building blocks

Understanding and solving problems, requires reflecting on the foundational elements of data representation, starting with a simple analogy
— a blank piece of paper. 

This space serves as our canvas for representing "pieces" of data, where a "piece" is any discrete unit of information. 

We'll represent these data pieces with closed shapes, using squares for simplicity, as each side is parallel to a dimension on the paper. 

Using a "squares on paper" analogy, imagine drawing two identical squares on the paper. They data pieces (squares) can be: 
* non-touching,
* partially touching,
* fully touching, or
* overlapping

<img width="524" height="411" alt="image" src="https://github.com/user-attachments/assets/f047cbc3-61f0-4059-9ca6-57373430cb71" />

To maintain the integrity of distinct data units, we'll dismiss the fourth scenario — overlapping, as it implies a fusion of data that defies our requirement for
discrete units. 

---

For consistency, we'll consider each square to be identical in size,
signifying that the data units, say numerical values, are equal in magnitude
and uniform in type.

Continuing under the premise that our data squares must not touch, the
paper will be filled with non-intersecting squares. However, data in
isolation is often meaningless. Thus, we introduce lines that bridge these
squares, connecting one piece of data to another. 

<img width="598" height="459" alt="image" src="https://github.com/user-attachments/assets/e26938e5-fed2-4222-b4f7-50e39729afc1" />

This network of squares and connecting lines forms the basic structure known as a **graph**. This
structure enables us to navigate from one data point to another, allowing data to reference other data, a principle
that underpins much of data organization and algorithm design.

When squares are placed adjacently, they naturally create a sequence. This
proximity can symbolize a related series of data units. We can extend this
sequence indefinitely, not just linearly, but also bi-dimensionally on our
two-dimensional paper, crafting rows and columns.

<img width="783" height="480" alt="image" src="https://github.com/user-attachments/assets/a221ca76-1ad2-479e-a805-d8cb8d53dc9d" />

This arrangement gives rise to another fundamental data structure known as
a **table**, or in computational terms, an **array**, or **matrix**. Arrays provide the
groundwork for organizing data into an accessible order or grid, allowing
for efficient storage and retrieval in computer systems.

The idea of assigning identity to some area of the paper is twofold:
• Draw a boundary
• Name/label it

The boundary is a small piece of the paper, represented by infinitely many
points and the name is a finite string of symbols, mapped to a natural
number.

<img width="516" height="180" alt="image" src="https://github.com/user-attachments/assets/e5e66c2f-8345-4421-813c-316c0a1ea0d3" />

Once we introduce labelling, we can then introduce the power of random
access memory. As humans, we can quickly point to the relevant area of the
paper and identify a square, but a computer is "blind" and thus has to
search the entire paper for the relevant item if necessary. 

By using Cartesian coordinates (numerical values indicating position) and showing how if we
provide the coordinates of the relevant items, the computer can implicitly
"select" separately on x and y coordinates and end up at the right slot by
"magic" (efficiently), we demonstrate the power of **random access** (RAM): a computer can jump directly to a piece of data via its coordinates rather than scanning everything. 

<img width="746" height="575" alt="image" src="https://github.com/user-attachments/assets/42e90cea-7be7-475c-b7cc-ac95752abfb4" />

In the end, our understanding of data, with all its intricacies, boils down to
two fundamental structures: 
* the interconnected nodes of graphs and
* the orderly rows and columns of tables.

This insight is as straightforward as it is deep, revealing the core frameworks that underpin all forms of data organization.

On paper or within the circuits of computers, our complex world of
information is ultimately navigated through these two simple, yet powerful
structures. It's a clear reflection of the binary essence of data representation
—either as individual points linked by relationships or as sequences laid
out in a grid—each with its unique way of organizing our digital landscape.

## 1.4 Solving problems with the State Space formulation

Problem-solving can be modeled as navigating through a **state space**. In this framework,
the solution process is conceptualized as a series of transitions from one
state to another, guided by a set of choices or actions.

### 1.4.1 State Space Representation 

In the context of state space, "space" refers to the set of all possible
configurations or conditions (states) that a system can occupy. It
encompasses every potential state the system can transition to based on its
variables, boundaries and constraints. 

The state space can be represented as a graph as follows: 

<img width="551" height="550" alt="image" src="https://github.com/user-attachments/assets/6c7cef1f-6de3-4458-abbf-dc0059a5f339" />

- **Current State (Si)**: This represents the current configuration or condition of the solution at any given moment. It encapsulates all the relevant information needed to describe the solution's status.

<img width="449" height="180" alt="image" src="https://github.com/user-attachments/assets/1b618ead-281e-4c0a-938c-66d0c4d8523e" />

- **Choices (Ci)**: From each state Si, there is a set of possible actions or choices (Ci) that can be applied to transition to other states:

<img width="270" height="56" alt="image" src="https://github.com/user-attachments/assets/10a57eb6-201e-4041-805f-251d803341d1" />

- **Transition Function (T)**: Each choice cij in the set Ci leads to a new state. Applying a choice cij to the current state Si results in a new state Sj. This can be represented by a transition function T such that:

<img width="167" height="53" alt="image" src="https://github.com/user-attachments/assets/14d6537b-7f09-4009-b655-ec731c0aa4a7" />

- **Final State (Sf)**: There can be many types of goals when considering a solution to a problem. A common goal is to reach a final state (Sf), where the problem is considered solved. The final state satisfies the conditions or criteria defined by the problem. We go from state to state applying choices until the success criteria are met. Other types of goals are specified in a later section.

---

**Reaching the Final State**: To determine if a final state has been reached,
specific conditions are checked. These could include:

• **Goal achievement**: Verifying if the desired outcome has been
attained (e.g., all puzzle pieces are in the correct positions).

• **Constraint satisfaction**: Ensuring all problem constraints are met
(e.g., all items are packed within the weight limit).

• **Optimization criteria**: Checking if the solution meets or exceeds a
defined threshold (e.g., the shortest path has been found).

• **Termination conditions**: Assessing if predefined stopping criteria
have been met (e.g., a maximum number of iterations has been
reached).

The specific conditions checked depend on the nature of the problem and
the desired solution characteristics. 

---

Because every problem can be cast into this state/choice/transition/goal structure, general techniques apply across domains:

- **Exhaustive search** — explore all states/transitions to guarantee optimality.

- **Divide and conquer** — split into independent subproblems, to later combine results.

- **Greedy algorithms** — pick the best-looking immediate choice at each step.

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

---

Core concepts for approaching problems before writing any code: understanding requirements, breaking problems into smaller pieces, and choosing a strategy (brute force, greedy, divide and conquer, dynamic programming, etc.).

Contents:

- Problem decomposition

- Pattern recognition

- Choosing an approach

- Common problem-solving heuristics

## 1.8 Conclusion

This chapter established the vocabulary for everything that follows: problems and their types, the two foundational data structures (graphs and tables), the state-space formulation (state, choices, transitions, final state), state-space navigation as graph traversal, problem decomposition via DAGs, and the different forms a "solution" can take. These concepts underpin the algorithms and techniques covered in later chapters.
