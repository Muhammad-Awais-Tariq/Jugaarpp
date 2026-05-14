# Programming Paradigms

---

## Functional Programming

In functional programming, **functions** are used to separate logic from data. Instead of bundling data and behaviour together, you pass data into pure functions that compute and return a result without modifying anything outside themselves.

**Example:**

```python
def remaining_fuel(initial, kilometers, ratio):
    return initial - kilometers * ratio
```

The function holds no data of its own — it simply performs a calculation on whatever is passed in. This separation makes code easier to test, reuse, and reason about.

---

## Object-Oriented Programming (OOP)

Rather than bundling an entire program into one file, OOP organises code into **objects** — self-contained units that group related data and behaviour together. Each object has:

- **Properties** — its data (what it knows)
- **Methods** — its functions (what it can do)

### The Four Pillars of OOP

| Pillar | Description |
|--------|-------------|
| **Encapsulation** | Each object manages its own data internally. For example, a `Lexer` and a `Parser` each hold their own properties independently, keeping concerns neatly separated. |
| **Abstraction** | Internal complexity is hidden behind a simple interface. Calling `Lexer().tokenize()` gives you tokens without exposing how tokenization works under the hood. |
| **Inheritance** | A child class inherits properties and methods from a parent class, enabling code reuse without duplication. |
| **Polymorphism** | The same method name can behave differently depending on which object calls it. A `sound()` method on a `Dog` object returns `"woof"`, while the same method on a `Cat` object returns `"meow"`. |

---

## OOP in Python

Below is a worked example of a `Payment` class that demonstrates class variables, instance variables, instance methods, and class methods.

```python
class Payment:
    initial_balance = 1000  # Class variable — shared across all instances

    def __init__(self, recipient, amount):
        self.recipient = recipient  # Instance variable — unique to each object
        self.amount = amount

    def check_balance(self):
        """Returns the remaining balance after this payment."""
        return Payment.initial_balance - self.amount

    @classmethod
    def update_balance(cls, new_balance):
        """Updates the shared class-level balance directly."""
        cls.initial_balance = new_balance


# Creating an instance (object) of Payment
payment1 = Payment("Awais", 12)
print(payment1.check_balance())  # Output: 988

# Calling a class method — no instance needed
Payment.update_balance(2000)
print(Payment.initial_balance)  # Output: 2000
```

### Key Concepts from the Example

**Class Variable (`initial_balance`)**
Defined directly on the class, not inside `__init__`. It is shared across every instance — changing it via `update_balance()` affects all objects of that class.

**Instance Variables (`recipient`, `amount`)**
Defined inside `__init__` using `self`. Each object gets its own copy, so `payment1.amount` is independent of any other payment object.

**Instance Method (`check_balance`)**
Takes `self` as its first argument, giving it access to that specific object's data.

**Class Method (`update_balance`)**
Decorated with `@classmethod` and takes `cls` instead of `self`. It operates on the class itself rather than any individual instance, so it can be called directly on the class without creating an object first.