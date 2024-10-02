# Magic Methods

## Common Python Magic Methods

| **Magic Method** | **Description** | **Example** |
|-------------------|-----------------|-------------|
| `__init__`       | Initializes a new object. | ```python class Person: def __init__(self, name): self.name = name p = Person("Alice")``` |
| `__str__`        | Returns a string representation of the object for end-users. | ```python class Person: def __str__(self): return self.name p = Person("Alice") print(p)  # Output: Alice``` |
| `__repr__`       | Returns a string representation of the object for developers, ideally unambiguous. | ```python class Person: def __repr__(self): return f"Person(name={self.name})" p = Person("Alice") print(repr(p))  # Output: Person(name=Alice)``` |
| `__add__`        | Defines behavior for the addition operator (`+`). | ```python class Vector: def __init__(self, x, y): self.x = x self.y = y def __add__(self, other): return Vector(self.x + other.x, self.y + other.y) v1 = Vector(1, 2) v2 = Vector(3, 4) print(v1 + v2)  # Output: Vector(4, 6)``` |
| `__sub__`        | Defines behavior for the subtraction operator (`-`). | ```python class Vector: def __sub__(self, other): return Vector(self.x - other.x, self.y - other.y) v1 = Vector(5, 6) v2 = Vector(3, 4) print(v1 - v2)  # Output: Vector(2, 2)``` |
| `__mul__`        | Defines behavior for the multiplication operator (`*`). | ```python class Vector: def __mul__(self, scalar): return Vector(self.x * scalar, self.y * scalar) v = Vector(1, 2) print(v * 3)  # Output: Vector(3, 6)``` |
| `__len__`        | Defines behavior for the built-in `len()` function. | ```python class MyList: def __init__(self, items): self.items = items def __len__(self): return len(self.items) my_list = MyList([1, 2, 3]) print(len(my_list))  # Output: 3``` |
| `__getitem__`    | Allows indexing into an object using square brackets (`[]`). | ```python class MyList: def __getitem__(self, index): return self.items[index] my_list = MyList([1, 2, 3]) print(my_list[0])  # Output: 1``` |
| `__contains__`   | Defines behavior for the `in` operator. | ```python class MyList: def __contains__(self, item): return item in self.items my_list = MyList([1, 2, 3]) print(2 in my_list)  # Output: True``` |
| `__call__`       | Allows an instance of a class to be called as if it were a function. | ```python class Adder: def __call__(self, x, y): return x + y add = Adder() print(add(5, 3))  # Output: 8``` |

## Additional Magic Methods

- **`__del__`**: Called when an object is about to be destroyed.
- **`__iter__`**: Returns an iterator object for iteration.
- **`__next__`**: Returns the next value from an iterator.
- **`__eq__`, `__lt__`, `__gt__`, etc.**: Define behavior for comparison operators like equality (`==`) and greater than (`>`).

These magic methods enhance the functionality of classes in Python by allowing them to interact seamlessly with built-in operations and functions. Understanding and implementing these methods can significantly improve code readability and maintainability.

## `__str__` VS `__repr__`

The difference between the `__str__` and `__repr__` methods in Python lies primarily in their intended audience and purpose.

### Purpose and Audience

- **`__repr__`**: This method is designed for developers and is meant to provide a detailed, unambiguous string representation of an object. The goal is to be informative enough that the output can ideally be used to recreate the object using `eval()`. It is called by the built-in `repr()` function and when an object is inspected in an interactive shell. The output should be clear and precise, making it useful for debugging and development purposes[1][2][3].

- **`__str__`**: This method is aimed at end-users and provides a more user-friendly or informal string representation of an object. It is called by the built-in `str()` function and when an object is printed. The output from `__str__` should be easy to read and understand, focusing on presenting information in a way that is useful for the user rather than for debugging[2][4][5].

### Fallback Mechanism

If a class defines both methods, Python will use `__str__` when you call `print()` or `str()`. However, if `__str__` is not defined, Python will fall back to using `__repr__`. This means that having a well-defined `__repr__` can ensure that even if `__str__` is not implemented, you still get a meaningful representation of the object[1][3][5].

### Example

Here’s an example illustrating both methods in a class:

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __repr__(self):
        return f"Person(name={self.name!r}, age={self.age!r})"

    def __str__(self):
        return f"{self.name}, {self.age} years old"

# Creating an instance
p = Person("Alice", 30)

# Using __repr__
print(repr(p))  # Output: Person(name='Alice', age=30)

# Using __str__
print(str(p))   # Output: Alice, 30 years old
```

In this example:

- The output of `repr(p)` provides a detailed view useful for developers.
- The output of `str(p)` provides a concise and friendly description suitable for users.

In summary, use `__repr__` for detailed representations aimed at developers and debugging, while `__str__` should be used for user-friendly outputs.
