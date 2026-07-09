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

To maintain the integrity of distinct data units, we'll dismiss the fourth scenario — overlapping, as it implies a fusion of data that defies our requirement for discrete units. 

---

For consistency, we'll consider each square to be identical in size, signifying that the data units, say numerical values, are equal in magnitude and uniform in type.

Continuing under the premise that our data squares must not touch, the paper will be filled with non-intersecting squares. However, data in isolation is often meaningless. Thus, we introduce lines that bridge these squares, connecting one piece of data to another. 

<img width="598" height="459" alt="image" src="https://github.com/user-attachments/assets/e26938e5-fed2-4222-b4f7-50e39729afc1" />

This network of squares and connecting lines forms the basic structure known as a **graph**. This structure enables us to navigate from one data point to another, allowing data to reference other data, a principle
that underpins much of data organization and algorithm design.

When squares are placed adjacently, they naturally create a sequence. This proximity can symbolize a related series of data units. We can extend this sequence indefinitely, not just linearly, but also bi-dimensionally on our two-dimensional paper, crafting rows and columns.

<img width="783" height="480" alt="image" src="https://github.com/user-attachments/assets/a221ca76-1ad2-479e-a805-d8cb8d53dc9d" />

This arrangement gives rise to another fundamental data structure known as a **table**, or in computational terms, an **array**, or **matrix**. Arrays provide the groundwork for organizing data into an accessible order or grid, allowing for efficient storage and retrieval in computer systems.

The idea of assigning identity to some area of the paper is twofold:
• Draw a boundary
• Name/label it

The boundary is a small piece of the paper, represented by infinitely many points and the name is a finite string of symbols, mapped to a natural number.

<img width="516" height="180" alt="image" src="https://github.com/user-attachments/assets/e5e66c2f-8345-4421-813c-316c0a1ea0d3" />

Once we introduce labelling, we can then introduce the power of random access memory. As humans, we can quickly point to the relevant area of the paper and identify a square, but a computer is "blind" and thus has to search the entire paper for the relevant item if necessary. 

By using Cartesian coordinates (numerical values indicating position) and showing how if we provide the coordinates of the relevant items, the computer can implicitly "select" separately on x and y coordinates and end up at the right slot by "magic" (efficiently), we demonstrate the power of **random access** (RAM): a computer can jump directly to a piece of data via its coordinates rather than scanning everything. 

<img width="746" height="575" alt="image" src="https://github.com/user-attachments/assets/42e90cea-7be7-475c-b7cc-ac95752abfb4" />

In the end, our understanding of data, with all its intricacies, boils down to two fundamental structures: 
* the interconnected nodes of graphs and
* the orderly rows and columns of tables.

This insight is as straightforward as it is deep, revealing the core frameworks that underpin all forms of data organization.

On paper or within the circuits of computers, our complex world of information is ultimately navigated through these two simple, yet powerful structures. It's a clear reflection of the binary essence of data representation — either as individual points linked by relationships or as sequences laid out in a grid—each with its unique way of organizing our digital landscape.

## 1.4 Solving problems with the State Space formulation

Problem-solving can be modeled as navigating through a **state space**. In this framework, the solution process is conceptualized as a series of transitions from one state to another, guided by a set of choices or actions.

### 1.4.1 State Space Representation 

In the context of state space, "space" refers to the set of all possible configurations or conditions (states) that a system can occupy. It encompasses every potential state the system can transition to based on its variables, boundaries and constraints. 

The state space can be represented as a graph as follows: 

<img width="551" height="550" alt="image" src="https://github.com/user-attachments/assets/6c7cef1f-6de3-4458-abbf-dc0059a5f339" />

- **Current State (Si)**: This represents the current configuration or condition of the solution at any given moment. It encapsulates all the relevant information needed to describe the solution's status.

<img width="449" height="180" alt="image" src="https://github.com/user-attachments/assets/1b618ead-281e-4c0a-938c-66d0c4d8523e" />

- **Choices (Ci)**: From each state Si, there is a set of possible actions or choices (Ci) that can be applied to transition to other states:

<img width="270" height="56" alt="image" src="https://github.com/user-attachments/assets/10a57eb6-201e-4041-805f-251d803341d1" />

- **Transition Function (T)**: Each choice cij in the set Ci leads to a new state. Applying a choice cij to the current state Si results in a new state Sj. This can be represented by a transition function T such that:

<img width="167" height="53" alt="image" src="https://github.com/user-attachments/assets/14d6537b-7f09-4009-b655-ec731c0aa4a7" />

- **Final State (Sf)**: There can be many types of goals when considering a solution to a problem.

A common goal is to reach a final state (Sf), where the problem is considered solved. We go from state to state applying choices until the success criteria are met. The final state satisfies the conditions or criteria defined by the problem. Other types of goals are specified in a later section.

---

**Reaching the Final State**: To determine if a final state has been reached, specific conditions are checked. These could include:

• **Goal achievement**: Verifying if the desired outcome has been attained (e.g., all puzzle pieces are in the correct positions).

• **Constraint satisfaction**: Ensuring all problem constraints are met (e.g., all items are packed within the weight limit).

• **Optimization criteria**: Checking if the solution meets or exceeds a defined threshold (e.g., the shortest path has been found).

• **Termination conditions**: Assessing if predefined stopping criteria have been met (e.g., a maximum number of iterations has been reached).

The specific conditions checked depend on the nature of the problem and the desired solution characteristics. 

### 1.4.2 Universal Problem Structure

By assuming this state/choice/transition/goal structure, every problem can be considered a variant of this "master" problem. This universal representation helps in applying general problem-solving techniques and algorithms across different domains. Here are a few methods that can be used within this framework:

• **Greedy Algorithms**: At each state, choose the action that appears to be the best immediate option, hoping it leads to the optimal final state.

• **Exhaustive Search**: Explore all possible states and transitions to ensure that the optimal solution is found.

• **Divide and Conquer**: Break the problem into smaller subproblems, solve each independently and combine the results to form the final state.

• **Dynamic Programming**: Use previously computed solutions of subproblems to construct the solution for the current state, optimizing the process. Maze pathfinding maps directly onto this framework (initial position → moves → new position → goal position).

### Example: Pathfinding in a Maze
Let's apply this concept to a simple example: finding a path through a maze.

• Initial State (So): The starting position in the maze.

• Choices (Ci): The possible moves (up, down, left, right) from the current position.

• Transition Function (T): Applying a move to the current position results in a new position.

• Final State (S): The goal position in the maze.

<img width="553" height="565" alt="image" src="https://github.com/user-attachments/assets/23dfdc78-7b94-41f1-a805-404ca809ea9d" />

The solution involves navigating from the initial state to the final state by making a series of choices that transition through the state space of the maze. 

### 1.4.3 Summary 

By visualizing problems as navigating through a state space, we can apply a consistent and structured approach to problem-solving. Each problem is reduced to a sequence of state transitions, driven by choices, until the final state is reached. This abstraction is powerful and versatile, enabling the application of various algorithms and techniques to solve a wide array of problems. 

## 1.5 Navigating Through State Space as Graph Traversal

The concept of navigating through a state space can indeed be effectively considered as a traversal of a graph. This perspective allows us to leverage the rich set of tools and algorithms developed for graph theory to solve a wide range of problems.

### 1.5.1 Exploring the Graph

By viewing the state space as a graph, we can apply various graph traversal techniques to explore and find solutions to the problem. 

The following is a (non-exhaustive) list of graph traversal algorithms:
• Breadth-First Search (BFS)

• Depth-First Search (DFS)

• Dijkstra's Algorithm

• A* Algorithm (not covered) 

### 1.5.2 Advantages of Graph Traversal for State Space Navigation
• **Clarity and Structure**: Representing problems as graphs provides a clear and structured way to visualize and solve them.

• **Algorithmic Tools**: A wide range of well-established algorithms for graph traversal and pathfinding can be directly applied.

• **Optimization**: Graph-based methods allow for the optimization of solutions, such as finding the shortest or least costly path.

• **Scalability**: Graph algorithms are designed to handle large and complex state spaces efficiently. 

### 1.5.3 Summary 
Viewing the navigation through state space as a graph traversal provides a powerful and versatile framework for problem-solving. By representing states as **nodes** and transitions as **edges** we can apply various graph
traversal techniques to explore and solve problems effectively. This approach leverages the extensive body of knowledge and algorithms in graph theory, offering clarity, structure and efficiency in finding solutions

## 1.6 The structure of problem decomposition

Complex problems can be broken into subproblems represented as a **Directed Acyclic Graph (DAG)**, which helps visualize the relationships between different components of a problem.

<img width="585" height="476" alt="image" src="https://github.com/user-attachments/assets/fdb1ecdd-83cd-4b79-bc49-db059d0aab6f" />

In the DAG above:
• Nodes represent subproblems or components of the main problem.

• Edges represent dependencies or relationships between these components.

• The acyclic nature ensures there are no circular dependencies.

• The direction of edges indicates the flow of information or sequence of solving.

The DAG representation is a powerful tool in problem-solving as it provides a clear visual of the problem's structure, dependencies and potential solution paths.

This structure allows us to:
• Break down complex problems into manageable parts

• Understand the order in which these parts need to be addressed 

• Identify independent subproblems that can be solved in parallel

• Recognize shared subproblems to avoid redundant work

### 1.6.1 Conditions for Collapse into a DAG 
A graph representing a state space or problem can be considered to "collapse" into a Directed Acyclic Graph (DAG) under certain conditions. This transition often implies a simplification or restructuring of the problem, allowing for more efficient solutions. 
• **Acyclic Nature**: The graph must be acyclic, meaning there are no cycles or loops. Each state or node is visited only once, ensuring that the graph flows in one direction without revisiting any node.

• **Dependency Structure**: The problem can be decomposed into subproblems with dependencies that are strictly hierarchical. Each subproblem depends on the results of other subproblems in a way that avoids circular dependencies.

### 1.6.2 Implications of Collapsing into a DAG
When a problem's graph representation collapses into a DAG, this restructuring provides several advantages:
• **Subproblem Definition**: The problem is now decomposed into smaller, manageable subproblems. Each node (or state) in the DAG represents a subproblem that contributes to the overall solution.

• **Topological Ordering**: Subproblems have a **strictly hierarchical dependency structure** (no circular dependencies). The DAG allows for a “topological sorting” of nodes, providing an order in which subproblems should be solved. This order respects the dependencies and ensures that each subproblem is solved before it is needed by other subproblems.

• **Efficiency in Problem-Solving**: With a DAG, we can apply dynamic programming and memoization techniques. Since the graph is acyclic, we can store the results of subproblems and reuse them, avoiding redundant computations. 

### 1.6.3 Equivalence of DAG Collapse and Subproblem Decomposition 
The collapse of a graph into a DAG is effectively equivalent to recognizing that the problem can be decomposed into subproblems. Here’s why:
• **Hierarchical Subproblems**: A DAG inherently represents a hierarchy or order of subproblems. Each node depends on the results of its predecessors, aligning with the concept of solving smaller problems to build up to the solution of the larger problem.

• **No Cycles**: The absence of cycles ensures that there is a definitive direction to the problem-solving process, similar to how subproblems are solved sequentially without looping back.

• **Reusability of Solutions**: In a DAG, once a subproblem is solved, its solution can be reused by any other subproblem that depends on it. This is a fundamental aspect of dynamic programming. 

### 1.6.4 Example: Dynamic Programming
Consider the classic example of the Fibonacci sequence, where each number is the sum of the two preceding ones:

<img width="301" height="43" alt="image" src="https://github.com/user-attachments/assets/d5abe114-ae51-4c39-996c-57ae0e7a93a8" />

• **Graph Representation**: Initially, we might represent this with a graph where each node corresponds to a Fibonacci number and edges represent the dependency (e.g., F'n` depends on F'n-1` and F'n-2`).

• **DAG Structure**: Though visualized as a tree, this graph is inherently a DAG because there are overlapping (repeated) subproblems and there are no cycles – once a Fibonacci number is computed, it is used by the subsequent numbers without revisiting.

• **Subproblem Decomposition**: Each Fibonacci number is a subproblem that depends on the solutions to two smaller subproblems. Dynamic programming can be used to compute each number efficiently by storing and reusing previously computed values. 

<img width="796" height="375" alt="image" src="https://github.com/user-attachments/assets/98d61eb0-dcc3-41de-b9c3-61560b7d315d" />

### 1.6.5 Summary
A problem's graph representation collapses into a DAG when it can be structured into a hierarchy of subproblems with no cyclic dependencies. This transformation indicates that the problem can be decomposed into manageable subproblems, facilitating the use of efficient problem-solving techniques like dynamic programming.

The DAG structure provides a clear order for solving subproblems, ensuring that each subproblem's solution is available when needed by other dependent subproblems. This equivalence highlights the powerful synergy between graph theory and algorithm design in optimizing complex problem-solving processes. 

The Fibonacci sequence illustrates this: it looks like a tree of recursive calls, but is really a DAG with overlapping subproblems (`Fn` depends on `Fn-1` and `Fn-2`), which is exactly why memoizing previously computed values makes it efficient.

## 1.7 What is a solution?

A solution is a satisfactory answer or resolution to a problem. It bridges the gap between the current state and the desired state while adhering to the given constraints. In the context of computational problems, a solution typically has the following characteristics:
• **Correctness**: A correct solution ensures that the problem is
accurately addressed as per the given requirements.

• **Efficiency**: Efficient solutions save time and resources, making them practical for real-world applications.

• **Completeness**: A complete solution works for all possible valid inputs, ensuring reliability.

• **Clarity**: Clear solutions are easier to understand, implement and maintain.

• **Robustness**: Robust solutions handle unexpected inputs gracefully, preventing failures.

• **Scalability**: Scalable solutions perform well even as the problem size grows, ensuring long-term usability.

Often, there might be multiple valid solutions to a problem, each with its trade-offs in terms of these characteristics. The choice of the best solution typically depends on the specific context and requirements of the situation. Understanding what constitutes a solution is crucial in problem-solving, as it guides the development of algorithms and helps in evaluating different approaches.

### 1.7.1 Types of Solutions in State Space 
In the context of a graph representation of a problem, a solution can take various forms depending on the nature of the problem and the specific requirements. Within the state-space framework, a "solution" can take several forms (different interpretations):


**Single Final State (S'f')** — one specific goal state (e.g., the maze exit).
• **Definition**: A single, specific state that signifies the completion or solution of the problem.

• **Example**: In a maze-solving problem, reaching the exit cell (S'f') represents the solution.

• **Graph Representation**: The solution is a path from the initial state (S'o') to this final state (S'f').

<img width="443" height="295" alt="image" src="https://github.com/user-attachments/assets/dac36fd3-8308-401d-8f9a-ea1560f264b9" />

**Set of Final States ( )** — any of several acceptable end states (e.g., any winning score in a game).
• **Definition**: A collection of acceptable final states, any of which would be considered a valid solution.

• **Example**: In a game, reaching any of several winning states could be considered a solution. For example, in football the states could be encoded as (number of goals by team A, number of goals by team B). So the set 
of possible winning states is (1, 0), (2, 0), (2, 1), (3, 2)…

• **Graph Representation**: The solution includes multiple paths from the initial state (S'o') to any of the states in the set F.




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
