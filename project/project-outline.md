### **Overall Project Stack Assumption**
*   **Source Language:** A simplified, C-like or Pascal-like language (e.g., "MiniJava", "TinyC").
*   **Implementation Language:** C++, Rust, or Python (for rapid prototyping).
*   **Target:** x86-64 assembly (NASM/GAS syntax).
*   **Platform:** Linux (for clean SysV ABI usage).

---

### **Milestone Plan**

#### **Sprint 1: Project Foundation & Lexical Analysis**
*   **Goal:** Establish the project and process the raw source code into tokens.
*   **Key Deliverables:**
    1.  Project repository (Git) with a clear build system (Make/CMake/Cargo).
    2.  Formal specification for the *source language* (lexical elements).
    3.  A working **lexer (scanner)** that reads a source file and outputs a list of tokens (e.g., `INT_LITERAL: 42`, `IDENTIFIER: "foo"`, `KEYWORD: "if"`).
    4.  Test suite with valid and invalid token streams.
*   **Stretch Goal:** Implement a preprocessor for comments and simple `#define` macros.

#### **Sprint 2: Syntax Analysis & Abstract Syntax Tree**
*   **Goal:** Define the grammar and build a parser to create an Abstract Syntax Tree (AST).
*   **Key Deliverables:**
    1.  Formal **Context-Free Grammar** (CFG) for the language.
    2.  A working **parser** (likely recursive descent) that consumes tokens from the lexer.
    3.  Parser constructs and outputs a well-defined **AST** data structure in memory.
    4.  Visualizer or pretty-printer for the AST (to .dot or text).
    5.  Test suite with syntactically correct and incorrect programs.
*   **Stretch Goal:** Implement robust error recovery in the parser.

#### **Sprint 3: Semantic Analysis & Symbol Table**
*   **Goal:** Move from syntax to meaning. Validate declarations, types, and scopes.
*   **Key Deliverables:**
    1.  A **symbol table** data structure supporting nested scopes (e.g., for blocks, functions).
    2.  **Semantic analyzer** that traverses the AST to:
        *   Populate the symbol table with variable/function declarations.
        *   Perform type checking on expressions and assignments.
        *   Verify function call arguments match signatures.
    3.  Meaningful error messages for semantic violations (e.g., "Undeclared variable `x`", "Type mismatch in assignment").
    4.  A validated, "decorated" AST, ready for code generation.
*   **Stretch Goal:** Implement basic type inference for constants.

#### **Sprint 4: Intermediate Representation & Simple Code Generation**
*   **Goal:** Introduce a platform-independent intermediate step and generate simple sequences.
*   **Key Deliverables:**
    1.  Design and implement a simple **Intermediate Representation (IR)**. (e.g., 3-address code, a custom instruction set, or use LLVM Lite if the language is C++).
    2.  First **code generator** that traverses the decorated AST and produces IR for:
        *   Arithmetic and logical expressions.
        *   Variable assignments (global/local).
        *   Simple control flow (e.g., `if-goto` style).
    3.  A working pipeline: `Source -> AST -> IR`.
    4.  Textual dumper for the IR.
*   **Stretch Goal:** Implement a very basic peephole optimizer on the IR.

#### **Sprint 5: x86-64 Backend Foundation & Function Prologues/Epilogues**
*   **Goal:** Generate real x86-64 assembly for the core runtime environment.
*   **Key Deliverables:**
    1.  **Stack Frame Management:** Code generation for function prologues (push `rbp`, move `rsp`, allocate space) and epilogues following the **System V AMD64 ABI**.
    2.  **Variable Storage:** Map IR temporaries and local variables to stack positions relative to `rbp`.
    3.  **Code generator** that can translate IR for simple **functions** (with parameters and locals) and **return statements** into correct assembly.
    4.  A small hand-written **runtime library** in assembly (e.g., `print_int`, `read_int`) and understand linking.
    5.  First **end-to-end compile & run** of a simple function (e.g., `func add(a, b) { return a + b; }`).
*   **Stretch Goal:** Implement simple register allocation (e.g., using `rax`, `rbx`, `rcx`, `rdx` as fixed registers).

#### **Sprint 6: Control Flow & Complex Expressions**
*   **Goal:** Compile complex language constructs.
*   **Key Deliverables:**
    1.  **Conditionals:** Full implementation of `if`, `if-else`, and relational operators (`<`, `>`, `==`), using conditional jumps (`jge`, `jne`, etc.).
    2.  **Loops:** Implementation of `while` and `for` loops.
    3.  **Logical Operators:** Short-circuit evaluation for `&&` and `||`.
    4.  **Complex Expressions:** Efficient code generation for nested expressions with correct operator precedence.
    5.  Test suite with programs using these control structures.
*   **Stretch Goal:** Implement `break` and `continue` statements.

#### **Sprint 7: Advanced Features & Optimizations**
*   **Goal:** Integrate remaining high-level features and introduce optimizations.
*   **Key Deliverables:**
    1.  **Arrays:** Support for static or stack-allocated arrays (calculate offsets).
    2.  **System Integration:** Generate code to call external C library functions (e.g., `printf`, `malloc`) following the ABI.
    3.  **Basic Optimizations:** Implement at least one optimization pass (e.g., constant folding/propagation on the IR, or dead code elimination).
    4.  A non-trivial demo program (e.g., a recursive factorial or a small sorting algorithm) that compiles and runs.
*   **Stretch Goal:** Implement simple inlining for small functions.

#### **Sprint 8: Integration, Polish, and Final Demo**
*   **Goal:** Create a robust, user-friendly compiler tool and prepare final deliverables.
*   **Key Deliverables:**
    1.  **Command-Line Interface:** A clean `./mycc [options] <sourcefile>` interface with flags (`-o`, `-S`, `--help`).
    2.  **Robust Error Handling:** Consolidated error reporting across all stages with source line and column numbers.
    3.  **Comprehensive Testing:** Final test suite including "good" programs (to verify output) and "bad" programs (to verify error messages).
    4.  **Documentation:** A final README with build instructions, language specification, and a quickstart guide.
    5.  **Final Demo:** A showcase program written in your new language that demonstrates all key features, compiled by your compiler, and executed natively.
*   **Stretch Goal:** Create a simple benchmark comparing the performance of your compiled code against an equivalent C program.

---

### **Success Tips for the Team:**
1.  **Version Control:** Use Git aggressively. Branch per feature, commit often, write meaningful messages.
2.  **Testing First:** For each milestone, write a small test program *before* implementing the feature.
3.  **Leverage Tools:** Use parser generators (Flex/Bison, ANTLR), but understanding the manual implementation is key.
4.  **Reference:** Keep the **System V AMD64 ABI** document and an **x86-64 instruction set reference** handy at all times.
5.  **Start Simple:** Get a "hello world" of your language (e.g., a program that just returns a constant) working end-to-end as early as Sprint 5. This builds morale and validates the toolchain.
