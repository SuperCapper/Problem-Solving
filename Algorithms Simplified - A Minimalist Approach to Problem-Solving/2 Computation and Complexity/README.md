# 2. Computation and Complexity

Summary of Chapter 2 from *Algorithms Simplified: A Minimalist Approach to Problem-Solving* (Rohith B V).

## 2.1 What is an algorithm?

An algorithm is a set of rules for solving a problem — in state-space terms, the rules for navigating the state space efficiently to a solution. A few core algorithmic approaches:

- **Greedy algorithms** — take the locally optimal choice at each step, hoping it leads to a global optimum.
- **Divide and conquer** — split the problem into independent subproblems, solve each recursively, then combine results (visualized as splitting a graph into disjoint subgraphs).
- **Memoization and caching** — cache the result of a subproblem the first time it's computed, and reuse it if the same subproblem recurs (illustrated with the "cinnamon" baking analogy: buy cinnamon once, reuse it for both the cake and the buns instead of re-buying).
- **Dynamic Programming (DP)** — combines graph traversal with memoization: break the problem into subproblems, solve each exactly once, store results in a table, and reuse them. DP goes further than plain memoization by also finding the optimal *order* to traverse the state space to minimize time/space.

## 2.2 What is a program? (barebones)

A program is a set of instructions telling a computer how to perform a task. The chapter covers Python basics as the core building blocks of any program:

- **Branches** — `if`/`elif`/`else` and `match`/`case` for conditional control flow.
- **Loops** — `for` loops (known iteration count), `while` loops (condition-driven), and `do-while` loops (simulated in Python; guarantees at least one execution).
- **Variables** — containers for storing data.
- **I/O** — reading input and printing output.
- **Operations** — arithmetic (`+ - * /`, modulus, exponentiation), logical (`and`/`or`/`not`), and bitwise (mentioned but not covered in depth).
- **Methods (functions)** — reusable, named blocks of code with parameters and a body.
- **Recursion** — a function calling itself, with a base case (stops recursion) and a recursive case (breaks the problem down further), illustrated with a factorial example. Pros: elegant for naturally recursive problems (e.g., tree traversal). Cons: risk of stack overflow on deep recursion, and can be less efficient than iterative solutions.
- **Execution** — explained via a "carrot soup" analogy: the cook (CPU) and gravity/water system (another executing agent) can work in parallel, mirroring parallel execution across CPU cores.
- **The Execution Stack** — the call stack manages function calls LIFO; each call pushes a stack frame (local variables, arguments, return address) that's popped on completion. The call stack's LIFO behavior is directly analogous to how Depth-First Search (DFS) manages traversal.
- **Program as a Graph** — programs can be modeled as graphs where nodes are functions/methods and edges are calls between them, clarifying control flow and call hierarchies.
- **Universal Nature of Graph Representations** — graphs recur everywhere in CS (control flow, networks, I/O flowcharts) because nodes+edges give a unified way to model states and transitions.

## 2.3 What is a process?

A process is the smallest unit of CPU execution — a "program in execution," with its own program counter, stack, registers, and memory. In the carrot-soup analogy, "filling the pot" and "cutting carrots" are two separate processes.

- **Concurrent execution** — multiple processes managed at once, via true parallelism (multiple processors) or multitasking (time-slicing a single processor).
- **Multiprocessing advantages** — better performance through concurrency, and more responsive applications (e.g., a GUI staying responsive while background work runs).
- **Challenges** — race conditions (unpredictable results from concurrent access to shared data), deadlocks (processes waiting on each other indefinitely), and the need for synchronization to prevent both.

## 2.4 What is complexity?

Complexity measures the resources (time and space) an algorithm needs to solve a problem, and how that scales with input size.

- **Big O notation** — describes the worst-case growth rate of an algorithm's running time as a function of input size (an upper bound), allowing abstract comparison between algorithms independent of hardware.
- **Reasoning about Big O**:
  - **Dominating terms** — keep only the fastest-growing term as input size grows (e.g., `T(n) = 3n² + 20n + 100` is `O(n²)`). Growth order: `Constants < Logarithms < Polynomials < Exponentials`, i.e. `O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ)`.
  - **Limits** — more rigorously, `f(n) = O(g(n))` if `lim(n→∞) f(n)/g(n)` is finite.
- **Common complexity classes**: `O(1)` constant (e.g., array index access), `O(log n)` logarithmic (e.g., binary search), `O(n)` linear (e.g., array traversal), `O(n log n)` log-linear (e.g., mergesort/quicksort average case), `O(n²)` quadratic (e.g., bubble/insertion sort), `O(2ⁿ)` exponential (e.g., naive recursive Fibonacci).
- **Analyzing time complexity**: identify basic operations → count them as a function of input size → find the dominant term → express in Big O, dropping constants and lower-order terms.
- **Space complexity** — memory used by an algorithm, split into input space and auxiliary space (e.g., temporary variables, recursion stack); analyzed with the same Big O notation.
- **Time/space trade-offs** — memoization trades space for time; richer data structures (e.g., hash tables) trade memory for speed; some algorithms (e.g., counting sort) trade extra space for better time complexity.

## 2.5 What is a Turing Machine?

A Turing Machine (Alan Turing, 1936) is the foundational theoretical model of computation, consisting of:

- **Tape** — infinite memory divided into cells holding symbols.
- **Head** — reads/writes symbols and moves left or right along the tape.
- **State register** — holds the machine's current state (one of finitely many).
- **Transition function** — given the current state and symbol read, determines the new state, the symbol to write, and which direction to move.

**Computability**: a problem is "computable" if a Turing Machine can solve it — this defines the theoretical limits of computation. Modern computers and programming languages are practical (finite) implementations of this idealized, symbol-manipulating model.

## 2.6 Conclusion

This chapter covered the building blocks of computation and complexity: algorithmic approaches (greedy, divide and conquer, memoization, DP), the core elements of programs (branches, loops, variables, functions, recursion), program execution (the call stack, programs as call graphs), processes and concurrency, how to reason about time and space complexity via Big O, and the Turing Machine as the theoretical basis for what is computable. These fundamentals underpin the algorithmic thinking developed in later chapters.
