# Semantic Analyzer

<em>A semantic analyzer for a custom programming language with support for type checking, scope management, and symbol table generation</em>

---

## Table of Contents

- [Semantic Analyzer](#semantic-analyzer)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Architecture](#architecture)
  - [Features](#features)
  - [Technology Stack](#technology-stack)
  - [Language Specification](#language-specification)
  - [Project Structure](#project-structure)
  - [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
    - [Usage](#usage)
  - [Examples](#examples)
  - [License](#license)
  - [Contact](#contact)

---

## Overview

**Semantic Analyzer** is a Python-based semantic analysis tool designed to validate source code written in a custom programming language. It performs comprehensive semantic checks including type validation, variable declaration verification, scope management, and function return type checking.

**Main functionalities:**
- Type checking for variables and function returns
- Scope-aware symbol table management (global and local scopes)
- Variable declaration and usage validation
- Function parameter and return type verification
- Control structure validation (if, while)
- Expression type inference

---

## Architecture

**Language Parser:**
- **Framework:** Custom implementation using regular expressions
- **Language:** Python 3
- **Design Pattern:** Modular separation of concerns (Analyzer, Symbol Table, Utilities)
- **Analysis Type:** Semantic analysis with single-pass parsing

**Core Components:**
- **AnalizadorCodigo (CodeAnalyzer):** Main semantic analysis engine (309 lines)
- **TablaSimbolos (SymbolTable):** Symbol table with scope management (59 lines)
- **UtilidadesArchivo (FileUtils):** File I/O utilities (26 lines)

---

## Features

| Category | Description |
| :-------- | :----------- |
| ✅ **Type Validation** | Validates variable types (`int`, `float`, `string`, `void`) and ensures type consistency in assignments |
| 🔍 **Semantic Checks** | Detects undeclared variables, type mismatches, and redeclarations within the same scope |
| 🎯 **Scope Management** | Implements hierarchical scope system (global and function-local) with proper variable resolution |
| 🔄 **Function Analysis** | Verifies function return types, validates parameters, and ensures non-void functions have return statements |
| 📊 **Symbol Table** | Generates and displays a comprehensive symbol table with all variables and functions |
| ⚡ **Control Structures** | Validates variables used in `if` and `while` conditions |
| 🧮 **Expression Analysis** | Infers types from arithmetic expressions and validates operand compatibility |

---

## Technology Stack

**Core Dependencies:**
- **Python 3** - Main programming language
- **re (Regular Expressions)** - Pattern matching for lexical analysis

**Supported Data Types:**
- `int` - Integer numbers
- `float` - Floating-point numbers
- `string` - Text strings
- `void` - No return type (functions only)

**Reserved Keywords:**
- `if`, `else`, `while`, `return`

---

## Language Specification

The analyzer validates code written in a custom C-like language with the following syntax:

**Variable Declaration:**
```c
int x;
float y;
string name;
```

**Variable Assignment:**
```c
x = 10;
y = 3.14;
name = "Hello";
```

**Function Declaration:**
```c
int sum(int a, int b) {
    return a + b;
}

void greet(string name) {
    // no return needed for void
}
```

**Control Structures:**
```c
if (x > 0) {
    // code
}

while (x < 10) {
    // code
}
```

---

## Project Structure

```sh
semantic-analyzer/
├── main.py                      # Entry point
├── analizador_codigo.py         # Main semantic analyzer engine
├── tabla_simbolos.py            # Symbol table implementation
├── utilidades.py                # File utilities
├── Funcion1.txt                 # Test case: valid function
├── Funcion2.txt                 # Test case: syntax errors
├── Funcion3.txt                 # Test case: incomplete function
├── Funcion4.txt                 # Test case: semantic errors
└── README.md                    # Documentation
```

---

## Getting Started

### Prerequisites

- **Python** 3.6 or higher

### Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/isaacmendezr/semantic-analyzer.git
   cd semantic-analyzer
   ```

2. No additional dependencies required (uses Python standard library only)

### Usage

1. Run the analyzer with a test file:
   ```sh
   python main.py
   ```

2. By default, it analyzes `Funcion4.txt`. To analyze a different file, edit `main.py`:
   ```python
   archivo = "Funcion1.txt"  # Change to your desired file
   ```

3. The analyzer will output:
   - The source code content
   - Any semantic errors found (with line numbers)
   - A symbol table showing all declared variables and functions

---

## Examples

**Valid Code (Funcion1.txt):**
```c
int funcion(int x){
 return x + 5;
}
```
Output: `No hay errores en el codigo fuente.`

**Code with Semantic Errors (Funcion4.txt):**
```c
x = 40  // Error: 'x' not declared

int funcion(float v, string n){
    if (v > 0.0){
        n = "Mayor"
        x = x + 5
    }
    return n  // Error: returns string but function is int
}
```
Output: 
```
Error – Linea 1: Variable 'x' no declarada.
Error – Linea 9: Tipo de retorno no coincide...
```

**Symbol Table Output:**
```
Tabla de Símbolos:
Nombre               Tipo            Alcance   
=============================================
funcion              Función (int)   funcion   
v                    float           funcion   
n                    string          funcion   
```

---

## License

Academic project developed for educational purposes.

## Contact

**Developer:** Isaac Méndez  
**Repository:** [https://github.com/isaacmendezr/semantic-analyzer](https://github.com/isaacmendezr/semantic-analyzer)

---

**Note:** This semantic analyzer is designed specifically for an academic custom language and is not intended with standard programming languages.
