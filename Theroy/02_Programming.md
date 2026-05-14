# The Need for Programming

A computer's **control unit** is composed of logic gates. It reads binary instructions and executes a specific operation for each one. For example, the instruction `1001` might be mapped to the addition operation — whenever the control unit encounters `1001`, it adds two numbers.

Program execution is a two-stage cycle:
1. **Fetch** — retrieve the instruction
2. **Execute** — carry out the action and save the result

## The Problem

In the early days of computing, programmers had to input raw machine code (1s and 0s) directly. This was done through physical means such as toggle switches and punch cards — a tedious and error-prone process.

## The Solution: Compilers

The solution was the **compiler** — software that translates human-readable code into binary machine code. The process works like this:

1. A programmer writes **source code** in a human-readable language
2. The **compiler** reads that source code
3. It outputs **machine code** (binary) that the CPU can execute directly

---

# How a Compiler Works: The Interpretation Pipeline

## Stage 1 — Lexical Analysis (Tokenization)

The first stage breaks raw source code into **tokens** — small labelled units of meaning. Each token stores two things:
- Its **value** (the literal text)
- Its **type** (what kind of thing it is)

**Example:**

Input:
```
1 + 3
```

Output (token list):
```
[ Token(1, INT), Token(+, OP), Token(3, INT) ]
```

This token list is then passed to the next stage: the parser.

---

## Stage 2 — Parsing

The parser takes the token list and checks whether it forms a valid, meaningful structure according to a set of **grammar rules**. In short: lexical analysis breaks code into words; parsing checks that those words form valid sentences.

### Writing Grammar Rules: BNF (Backus-Naur Form)

BNF is a standard notation for defining grammar rules. It uses two types of elements:
- **Non-terminals** — abstract placeholders written in `<angle brackets>`, e.g. `<expression>`
- **Terminals** — literal values like numbers and operators

The `|` symbol means **"or"**, and `:=` means **"is defined as"**.

**Example grammar:**

```
<expression> := <term> + <expression>
              | <term> - <expression>
              | <term>

<term>       := <factor> * <term>
              | <factor> / <term>
              | <factor>

<factor>     := <integer>
<integer>    := 0 | 1 | 2 | 3 | ... n
```

An alternative, more compact notation uses `*` to mean "zero or more repetitions":

```
E = Term ((+ | -) Term)*
```

---

### Key Concepts

**Expression**
Any value, or a term combined with another term via addition or subtraction.

**Parse Tree**
The parser converts a valid expression into a **binary tree**, which represents the order of operations explicitly.

For `1 + 2 * 5`, the parser respects operator precedence and produces:

```
1 + [2 * 5]
```

Which maps to this tree:

```
        +
       / \
      1   *
         / \
        2   5
```

- **Root node:** `+`
- **Left child:** `1`
- **Right child:** `*`
  - **Left child:** `2`
  - **Right child:** `5`

The tree makes evaluation order unambiguous — the deepest nodes (`2 * 5`) are evaluated first, and their result is then added to `1`.