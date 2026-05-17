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

## Traversal
### Preorder
it means first the root then their will b left and the right subtree will b traversed
A B  D E C 

IF we have expression like 1 + 2 * 3 after the step one breaking it into token the step two will b converting them into the tree strucutre
   +
  /  \
  1   *
     / \
     2  3
Traverssing it will effect how we evaluate it

### Postorder
it mean first we will traverse left and then right and then will move to the root
taking expression it will b 
123*+

The post order allow us to compute like
1*8+7
 +
 / \
 *  7 
/ \
1   8

it will be 18*7+ this is our interpretation of the expression 

This is same for the variable assigment as well like
a = b

   =
  / \
  a  b

### Binary tree in python
```python
class node:
    def __init__(self,value):
        self.value = value
        self.left = None
        self.right = None  # These represent left and right childs

class tree:
    def __init__(self,root):
        self.root = node(root)

    def preorder(self , start , record):  #start represting the starting node in the preorder traversal ,record will b empty list in the start
        if start is not none:
            record.append(start.value)   
            record  = self.preoder(self.left, record)  # we are computing the left subtree with recurssion first
            record = self.preoder(self.right, record) 
tree1 = tree(5)
tree.root.left = node(4)
tree.root.right = node(7)   #adding left and right childs
tree.preoder(tree.root,[])
#    5
#   / \
#  4   7
```