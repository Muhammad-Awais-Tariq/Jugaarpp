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

