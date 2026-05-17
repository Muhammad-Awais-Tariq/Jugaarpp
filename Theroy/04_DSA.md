# Data Structures: Stacks & Binary Trees

---

## 1. Stacks

A stack is a **Last In, First Out (LIFO)** data structure — think of a stack of plates: you
can only add a new plate on top, and you can only remove the top plate. You cannot insert or
remove from the middle or bottom.

**Real-world analogies:**
- Browser back button (each page you visit is pushed; going back pops it)
- Undo/Redo in text editors
- Function call stack in programming (when a function calls another function)

**Core operations:**
| Operation | Description |
|-----------|-------------|
| `push(item)` | Add an item to the top |
| `pop()` | Remove and return the top item |
| `peek()` | View the top item without removing it |
| `is_empty()` | Check whether the stack is empty |
| `size()` | Return the number of items in the stack |

```python
class Stack:
    def __init__(self):
        self.stack = []

    def push(self, item):
        self.stack.append(item)         # Add to the top

    def pop(self):
        if self.is_empty():
            raise IndexError("Pop from an empty stack")
        return self.stack.pop()         # Remove and return from the top

    def peek(self):
        if self.is_empty():
            raise IndexError("Peek at an empty stack")
        return self.stack[-1]           # View top without removing

    def is_empty(self):
        return len(self.stack) == 0

    def size(self):
        return len(self.stack)

    def __repr__(self):
        return f"Stack (top → bottom): {self.stack[::-1]}"   #its printing the entire array this function tells the print to print the value not the memory location of object


# --- Example Usage ---
s = Stack()
s.push(10)
s.push(20)
s.push(30)

print(s)           # Stack (top → bottom): [30, 20, 10]  #its being printed using __repr__
print(s.peek())    # 30  ← top item, not removed
print(s.pop())     # 30  ← removed from top
print(s.pop())     # 20
print(s.size())    # 1
```

> **Key fix from original:** `pop()` should *return* the removed value, and both `pop()` and
> `peek()` should guard against an empty stack.

---

## 2. Binary Trees

A **binary tree** is a hierarchical data structure where each node has **at most two children**,
referred to as the **left child** and the **right child**.

```
        A          ← Root node (top of the tree)
       / \
      B   C        ← Children of A; B and C are each roots of their own subtrees
     / \
    D   E          ← Leaf nodes (no children)
```

**Key terminology:**
- **Root** – the topmost node (no parent)
- **Leaf** – a node with no children
- **Subtree** – any node together with all its descendants (e.g. B, D, E form a subtree)
- **Height** – the longest path from root to a leaf

Binary trees are used in:
- Expression parsing and compilers
- File system hierarchies
- Database indexing (B-trees)
- Priority queues (heaps)

---

## 3. Tree Traversal

Traversal means visiting every node in the tree in a specific order. There are three classic
depth-first orders:

### 3.1 Preorder — Root → Left → Right

Visit the current node *before* its children. Good for copying a tree or generating prefix
notation for expressions.

**Order on our example tree:** `A → B → D → E → C`

**Expression tree example:**

```
    +
   / \
  1   *
     / \
     2   3
```

Preorder gives: `+ 1 * 2 3` — this is **prefix notation** (operator comes first).  
To evaluate: apply `+` to `1` and `(* 2 3)` → `1 + 6 = 7`.

---

### 3.2 Inorder — Left → Root → Right

Visit left subtree, then the current node, then right subtree. For a **Binary Search Tree (BST)**
this always produces values in *sorted order*.

**Order on our example tree:** `D → B → E → A → C`

**Expression tree example (same tree as above):**

Inorder gives: `1 + 2 * 3` — this is standard **infix notation**, the one we write normally.

---

### 3.3 Postorder — Left → Right → Root

Visit both children *before* the current node. Good for evaluating expressions and for deleting
a tree (children before parent).

**Order on our example tree:** `D → E → B → C → A`

**Expression tree example:**

```
      +
     / \
     *   7
    / \
    1   8
```

Postorder gives: `1 8 * 7 +` — this is **Reverse Polish (postfix) notation**.  
To evaluate: push operands onto a stack; when you see an operator, pop two operands and compute.
  - Push `1`, push `8`
  - See `*` → pop `8` and `1` → push `8` (= 1×8)
  - Push `7`
  - See `+` → pop `7` and `8` → result is `15`

**Variable assignment also maps naturally to a tree:**

```
a = b

    =
   / \
  a   b
```
Postorder: `a b =` — evaluate operands before applying the assignment operator.

---

## 4. Binary Tree in Python

```python
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None    # Left child
        self.right = None   # Right child


class BinaryTree:
    def __init__(self, root_value):
        self.root = Node(root_value)

    def preorder(self, start, record):
        """Root → Left → Right"""
        if start is not None:                              # Fixed: 'None' not 'none'
            record.append(start.value)
            record = self.preorder(start.left, record)    # Fixed: start.left, not self.left
            record = self.preorder(start.right, record)   # Fixed: start.right, not self.right
        return record

    def inorder(self, start, record):
        """Left → Root → Right"""
        if start is not None:
            record = self.inorder(start.left, record)
            record.append(start.value)
            record = self.inorder(start.right, record)
        return record

    def postorder(self, start, record):
        """Left → Right → Root"""
        if start is not None:
            record = self.postorder(start.left, record)
            record = self.postorder(start.right, record)
            record.append(start.value)                    # Fixed: this line was missing!
        return record


# --- Build the tree ---
#       5
#      / \
#     4   7

tree1 = BinaryTree(5)
tree1.root.left = Node(4)    # Fixed: tree1, not tree
tree1.root.right = Node(7)

# --- Traversals ---
print(tree1.preorder(tree1.root, []))   # [5, 4, 7]
print(tree1.inorder(tree1.root, []))    # [4, 5, 7]
print(tree1.postorder(tree1.root, []))  # [4, 7, 5]
```

---

## 5. Summary Table

| Traversal | Order | Use Case |
|-----------|-------|----------|
| Preorder | Root → Left → Right | Copy a tree, prefix expressions |
| Inorder | Left → Root → Right | Sorted output from BST, infix expressions |
| Postorder | Left → Right → Root | Delete a tree, postfix/RPN expressions |

---