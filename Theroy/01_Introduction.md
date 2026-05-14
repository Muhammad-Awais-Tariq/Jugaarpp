# How Computers Work

A ground-up overview of how computers function, from raw hardware to memory storage.

---

## Transistors & Binary

At the most fundamental level, a computer is built from **transistors** — tiny switches made of silicon and electrodes. Silicon is a semiconductor, meaning it allows or blocks electrical current depending on the voltage applied to it:

- When current **flows through**, the state is read as **1**
- When current **does not flow**, the state is read as **0**

This on/off behavior is the origin of **binary** — the language all computers speak.

---

## Logic Gates

Logic gates are the building blocks of computation. They take binary inputs (0s and 1s) and produce a binary output based on a defined rule. The core gates are:

| Gate | Behavior |
|------|----------|
| **NOT** | Inverts the input — `0 → 1` and `1 → 0` |
| **OR** | Outputs `1` if *at least one* input is `1`, otherwise `0` |
| **AND** | Outputs `1` only if *both* inputs are `1`, otherwise `0` |
| **XOR** | Outputs `1` if the inputs are *different*, and `0` if they are the same |

By combining these gates, computers can perform increasingly complex operations.

---

## Arithmetic in Binary

Computers don't use the base-10 (decimal) system we use in everyday life — they work entirely in **base-2 (binary)**. To perform arithmetic:

1. Decimal numbers are **converted to binary**
2. Operations are performed **on the binary values** using logic gates
3. The result is converted back as needed

For example, **binary addition** can be implemented using XOR and AND gates — this is the basis of a circuit called a **half adder**, and is how all arithmetic ultimately happens in hardware.

---

## Computer Memory

Computers store data using circuits called **SR latches** (Set-Reset latches). An SR latch has two control wires:

- **S (Set)** — used to write a value into memory
- **R (Reset)** — used to clear the stored value

The latch "remembers" its last state even after the input is removed. By chaining multiple latches together, a computer can store binary numbers of any length — each latch holds a single bit (`0` or `1`), and groups of latches hold full values. This is the foundation of **RAM** and all short-term storage.