# Mini Python Compiler using Flex and Bison

## Project Overview

This project implements a mini compiler for a subset of Python-like language. It demonstrates the complete compilation process by dividing it into multiple phases: Lexical Analysis, Syntax Analysis, Semantic Analysis, Abstract Syntax Tree generation, Intermediate Code Generation, Code Optimization, and Target Code Generation. Each phase is implemented and executed separately for clarity and understanding.

---

## Objectives

* To understand the working of different phases of a compiler
* To implement a compiler using Flex and Bison
* To convert high-level code into intermediate and low-level representations
* To analyze how expressions and control structures are processed internally

---

## Tools and Technologies

* Flex (Lexical Analyzer Generator)
* Bison (Parser Generator)
* C Programming Language
* GCC Compiler
* MSYS2 / Linux Terminal

---

## Project Structure

```
Mini-Python-Compiler/
│
├── 1-Token_and_Symbol_Table/
├── 2-Abstract_Syntax_Tree/
├── 3-Intermediate_Code_Generation/
├── 4-Code_Optimization/
├── 5-Target_Code_Generation/
└── README.md
```

---

# Phase 1: Lexical Analysis and Symbol Table

## Description

In this phase, the input program is read and divided into tokens such as identifiers, keywords, operators, and constants. A symbol table is also constructed to store information about variables.

## Implementation

* Implemented using a Flex file (`proj.l`)
* Generates `lex.yy.c` which performs tokenization

## Functionality

* Identifies tokens like identifiers, integers, operators
* Stores variables in a symbol table
* Maintains details such as name, value, scope, and line number

## Output

* Token stream representation
* Symbol table with variable information

---

# Phase 2: Syntax Analysis and Abstract Syntax Tree

## Description

This phase checks whether the sequence of tokens follows the grammar rules. It also builds an Abstract Syntax Tree (AST) representing the structure of the program.

## Implementation

* Implemented using a Bison file (`proj1.y`)
* Generates `proj1.tab.c` and `proj1.tab.h`

## Functionality

* Validates syntax using grammar rules
* Constructs AST for expressions and statements
* Represents hierarchical structure of the program

## Example Concept

Expression:

```
c = a + b + 100
```

AST structure:

```
     +
    / \
   + 100
  / \
 a   b
```

---

# Phase 3: Semantic Analysis

## Description

Semantic analysis ensures that the program is meaningful. It verifies variable usage, scope, and evaluates expressions.

## Implementation

* Integrated within parser actions
* Uses symbol table for validation

## Functionality

* Tracks variable declarations and usage
* Maintains scope (local/global)
* Evaluates expressions and updates values
* Detects basic semantic issues such as undeclared variables

## Output

* Updated symbol table with computed values
* Verified correctness of expressions

---

# Phase 4: Intermediate Code Generation

## Description

This phase converts the program into a machine-independent intermediate representation known as three-address code.

## Functionality

* Breaks complex expressions into simpler operations
* Uses temporary variables to store intermediate results
* Generates step-by-step instructions

## Example

Input:

```
c = a + b + 100
```

Intermediate Code:

```
t0 = a + b
t1 = t0 + 100
c = t1
```

## Control Flow Handling

Conditional statements are handled using labels and jumps.

Example:

```
t0 = a >= b
if not t0 goto L1
t1 = a + b
a = t1
L1:
```

---

# Phase 5: Code Optimization

## Description

This phase improves the intermediate code by reducing unnecessary computations and enhancing efficiency.

## Techniques Used

* Constant Folding
* Elimination of redundant computations
* Simplification of expressions

## Example

Before optimization:

```
t0 = 2 + 3
```

After optimization:

```
t0 = 5
```

---

# Phase 6: Target Code Generation

## Description

The optimized intermediate code is translated into a lower-level representation similar to assembly language.

## Functionality

* Converts instructions into register-based operations
* Produces machine-like instructions

## Example

```
MOV R1, a
ADD R1, b
MOV c, R1
```

---

# Execution Steps

1. Navigate to the required phase folder:

```
cd folder_name
```

2. Generate lexical analyzer:

```
flex proj.l
```

3. Generate parser:

```
bison -d proj1.y
```

4. Compile:

```
gcc lex.yy.c proj1.tab.c -o a.exe
```

5. Run:

```
./a.exe
```

---

# Conclusion

This project demonstrates the complete working of a compiler by implementing all major phases. It shows how high-level code is analyzed, structured, validated, and transformed into intermediate and target-level representations. The use of Flex and Bison simplifies the implementation of lexical and syntax analysis while providing a clear understanding of compiler design concepts.

# Authors
Dongeshwar Sudhiksha - 160123733148
Kommareddy Vishrutha Reddy - 160123733153
Pavani Manupati - 160123733158
Nagilla Meenakshi Kruthika Reddy - 160123733160
Sahithi Pathem - 160123733164

---
