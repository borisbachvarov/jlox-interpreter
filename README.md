# Lox Interpreter — Crafting Interpreters

A Java implementation of the **Lox** programming language, built by following Robert Nystrom's [Crafting Interpreters](https://craftinginterpreters.com/).

## Progress

- [x] **Chapter 4** — Scanning / Lexing
- [x] **Chapter 5** — Representing Code (AST + GenerateAst tool)
- [x] **Chapter 6** — Parsing Expressions
- [ ] **Chapter 7** — Evaluating Expressions
- [ ] **Chapter 8** — Statements and State
- [ ] ...

## Project Structure

```
craftinginterpreters/
├── lox/
│   └── com/craftinginterpreters/lox/
│       ├── Lox.java          # Entry point
│       ├── Scanner.java      # Lexer — turns source into tokens
│       ├── Token.java        # Token data class
│       ├── TokenType.java    # Enum of all token types
│       ├── Expr.java         # AST node definitions (auto-generated)
│       ├── Parser.java       # Recursive descent parser
│       └── AstPrinter.java   # Debug printer for AST nodes
└── tool/
    └── com/craftinginterpreters/tool/
        └── GenerateAst.java  # Code generation tool for Expr.java
```

## How to Build and Run

### Compile

From the `craftinginterpreters` root directory:

```bash
javac lox/com/craftinginterpreters/lox/*.java
```

### Run (REPL)

```bash
java -cp lox com.craftinginterpreters.lox.Lox
```

### Run a file

```bash
java -cp lox com.craftinginterpreters.lox.Lox path/to/script.lox
```

### Regenerate Expr.java

If you modify `GenerateAst.java`, recompile and rerun it:

```bash
javac tool/com/craftinginterpreters/tool/GenerateAst.java
java -cp tool com.craftinginterpreters.tool.GenerateAst lox/com/craftinginterpreters/lox
```

## Example Output

The parser currently prints the AST. For example:

```
> 10 - 3 * 2
(- 10.0 (* 3.0 2.0))

> (10 - 3) * 2
(* (group (- 10.0 3.0)) 2.0)

> 1 + 2 == 3
(== (+ 1.0 2.0) 3.0)
```

## About Lox

Lox is a dynamically typed, garbage-collected scripting language designed by Robert Nystrom for teaching purposes. It supports:

- Numbers, strings, booleans, nil
- Arithmetic and comparison operators
- Variables and scope
- Control flow (if, while, for)
- Functions and closures
- Classes and inheritance

## Reference

- Book: [https://craftinginterpreters.com](https://craftinginterpreters.com)
- Author: Robert Nystrom
