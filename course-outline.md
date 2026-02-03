## **Compiler Construction: Theory & Practice Course Syllabus**

### **Module 1: Foundations (Lectures 1-3)**

**Lecture 1: Introduction to Compilers & Course Overview**
*   What compilers do and why they matter
*   Historical context: FORTRAN to modern languages
*   The compilation pipeline: 7-phase model
*   **Project Kickoff:** Overview of the 8 milestones, language specification discussion
*   **Tools:** Introduction to Git, build systems, test frameworks

**Lecture 2: Lexical Analysis Theory**
*   Formal languages review: alphabets, strings, languages
*   Regular expressions and their limitations
*   Finite automata: NFA vs DFA
*   Implementing scanners: table-driven vs hand-coded
*   **Project Alignment:** Lecture before **Sprint 1** (Lexer implementation)

**Lecture 3: Parsing Foundations**
*   Context-free grammars: formal definition
*   Parse trees vs abstract syntax trees
*   Ambiguity and how to resolve it (operator precedence, associativity)
*   **Hands-on:** Writing a grammar for your project language
*   **Project Alignment:** Supports **Sprint 2** (Parser development)

### **Module 2: Syntax & Semantics (Lectures 4-7)**

**Lecture 4: Top-Down Parsing**
*   LL(k) grammars and recursive descent
*   Predictive parsing with FIRST/FOLLOW sets
*   Left recursion elimination
*   Error recovery in top-down parsers
*   **Project Alignment:** Practical guidance for **Sprint 2**

**Lecture 5: Bottom-Up Parsing & Parser Generators**
*   LR parsing concepts (shift-reduce)
*   Introduction to parser generators (Yacc/Bison, ANTLR)
*   When to use hand-written vs generated parsers
*   **Case Study:** Real language grammar snippets

**Lecture 6: Semantic Analysis I - Symbol Management**
*   The role of semantic analysis in compilation
*   Symbol table design: hashing, trees, scoped tables
*   Name resolution: lexical vs dynamic scoping
*   Type systems introduction
*   **Project Alignment:** Core theory for **Sprint 3**

**Lecture 7: Semantic Analysis II - Type Systems**
*   Type checking algorithms
*   Type inference basics
*   Attribute grammars for semantic analysis
*   Error reporting and recovery in semantic phase
*   **Project Alignment:** Implementation techniques for **Sprint 3**

### **Module 3: Intermediate Representations & Architecture (Lectures 8-11)**

**Lecture 8: Intermediate Representations**
*   Why use IR? Benefits for optimization and retargeting
*   Survey of IRs: AST, 3-address code, SSA form, LLVM IR
*   Design decisions for your project IR
*   **Project Alignment:** Foundation for **Sprint 4**

**Lecture 9: x86-64 Architecture Deep Dive I**
*   Registers and their roles (general purpose, special purpose)
*   Memory addressing modes
*   Basic instruction categories (data movement, arithmetic)
*   **Lab:** Reading and writing simple assembly by hand
*   **Project Alignment:** Essential for **Sprint 5**

**Lecture 10: x86-64 Architecture Deep Dive II**
*   Control flow instructions (jumps, conditional branches)
*   Function calling conventions (System V ABI)
*   Stack frame layout (return addresses, saved registers, locals)
*   **Project Alignment:** Critical for **Sprint 5** (function implementation)

**Lecture 11: Runtime Environments**
*   Memory layout: code, static data, heap, stack
*   Activation records and stack management
* **Heap management** (brief intro to malloc/free)
*   Calling external functions (linking with C libraries)
*   **Project Alignment:** Supports **Sprint 5 & 7**

### **Module 4: Code Generation (Lectures 12-15)**

**Lecture 12: Code Generation Fundamentals**
*   Translating AST/IR to machine instructions
*   Expression evaluation strategies (stack vs register machines)
*   Simple register allocation schemes
*   **Project Alignment:** Core of **Sprint 5 & 6**

**Lecture 13: Control Flow Translation**
*   Translating high-level control structures (if, while, for)
*   Boolean expression translation with short-circuiting
*   Label generation and management
*   **Project Alignment:** Directly supports **Sprint 6**

**Lecture 14: Advanced Code Generation**
*   Array and structure access
*   Function pointer implementation
*   **Project-specific features** (based on chosen language)

**Lecture 15: Optimization I - Local Techniques**
*   The optimization spectrum: when and what to optimize
*   Peephole optimization
*   Constant folding and propagation
*   Common subexpression elimination
*   **Project Alignment:** Theory for **Sprint 7** optimizations

### **Module 5: Advanced Topics & Project Integration (Lectures 16-18)**

**Lecture 16: Optimization II - Global Techniques**
*   Data flow analysis introduction
*   Liveness analysis and register allocation
*   Introduction to graph coloring
*   **Note:** Students implement only basics, but theory is valuable

**Lecture 17: Real-world Compiler Engineering**
*   Error handling across phases
*   Debug information generation
*   Compiler testing strategies
*   Performance profiling of generated code
*   **Project Alignment:** Polishing for **Sprint 8**

**Lecture 18: Course Wrap-up & Beyond**
*   Survey of modern compiler topics: JIT compilation, vectorization
*   Alternative architectures (RISC-V, ARM)
*   Domain-specific languages
*   **Project demos** and lessons learned
*   Career paths in compiler engineering

---

## **Key Learning Outcomes**

By the end of this course, students will be able to:
1. Explain each phase of the compilation pipeline
2. Design and implement a scanner and parser for a non-trivial language
3. Perform semantic analysis including type checking
4. Generate correct x86-64 assembly for complex language constructs
5. Apply basic optimization techniques
6. Test and debug a multi-phase compiler system
