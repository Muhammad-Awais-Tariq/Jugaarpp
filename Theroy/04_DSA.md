# Stacks
its like a stack of book or any stack in it we can add or remove the elements but we can only add and remove from the stack and not for any other way

```python
class stack:
    def __init__(self):
        self.stack = []
    def push(self , item):
        self.stack.append(item)

    def pop(self):
        self.stack.pop()

    def peek(self):
        return self.stack[-1]
```

# Binary Tree:
its a data strucutre that can have only have two childern and is used for traversal 

    a  # The top is the root nood the rest are childe nodes
   /  \
   B    C   # b d e are subtree as they are tree in a tree
  / \ 
  D  E


