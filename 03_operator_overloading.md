# operator overloading

## 1. Arithmetic Operators

### Addition (`+`)

You can overload the `+` operator by defining the `__add__` method.

```python
class Point:
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)

    def __str__(self):
        return f"({self.x}, {self.y})"

p1 = Point(1, 2)
p2 = Point(2, 3)
print(p1 + p2)  # Output: (3, 5)
```

### Subtraction (`-`)

Overload the `-` operator using the `__sub__` method.

```python
class Point:
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y

    def __sub__(self, other):
        return Point(self.x - other.x, self.y - other.y)

p1 = Point(5, 7)
p2 = Point(2, 3)
print(p1 - p2)  # Output: (3, 4)
```

### Multiplication (`*`)

Overload the `*` operator using the `__mul__` method.

```python
class Number:
    def __init__(self, value):
        self.value = value

    def __mul__(self, other):
        return Number(self.value * other.value)

n1 = Number(3)
n2 = Number(4)
print((n1 * n2).value)  # Output: 12
```

### Division (`/`)

Overload the `/` operator using the `__truediv__` method.

```python
class Number:
    def __init__(self, value):
        self.value = value

    def __truediv__(self, other):
        return Number(self.value / other.value)

n1 = Number(10)
n2 = Number(2)
print((n1 / n2).value)  # Output: 5.0
```

## 2. Comparison Operators

### Less Than (`<`)

You can overload the `<` operator using the `__lt__` method.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __lt__(self, other):
        return self.age < other.age

p1 = Person("Alice", 30)
p2 = Person("Bob", 25)
print(p1 < p2)  # Output: False
```

### Greater Than (`>`)

Overload the `>` operator using the `__gt__` method.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __gt__(self, other):
        return self.age > other.age

p1 = Person("Alice", 30)
p2 = Person("Bob", 25)
print(p1 > p2)  # Output: True
```

## 3. Equality Operators

### Equal To (`==`)

You can overload the `==` operator using the `__eq__` method.

```python
class Person:
    def __init__(self, name):
        self.name = name

    def __eq__(self, other):
        return self.name == other.name

p1 = Person("Alice")
p2 = Person("Alice")
print(p1 == p2)  # Output: True
```

## 4. Unary Operators

### Negation (`-`)

You can overload unary negation by defining the `__neg__` method.

```python
class Number:
    def __init__(self, value):
        self.value = value

    def __neg__(self):
        return Number(-self.value)

n = Number(5)
print((-n).value)  # Output: -5
```

## 5. Bitwise Operators

### Bitwise AND (`&`)

You can overload the `&` operator using the `__and__` method.

```python
class MyClass:
    def __init__(self, value):
        self.value = value

    def __and__(self, other):
        return MyClass(self.value & other.value)

a = MyClass(6)   # Binary: 110
b = MyClass(3)   # Binary: 011
c = a & b
print(c.value)   # Output: 2 (Binary: 010)
```

# `__truediv__` vs `__dev__`

The method `__truediv__` in Python is specifically designed to implement true division, distinguishing it from the older `__div__` method used in Python 2. Here’s a detailed explanation of why it is called `__truediv__` instead of just `__div__`.

## Background

1. **Python 2 vs. Python 3**:
   - In Python 2, the `/` operator performed classic division, which meant that dividing two integers would yield an integer result (floor division). The method associated with this operation was `__div__`.
   - Python 3 introduced a clearer distinction between true division and floor division. The `/` operator was redefined to always perform true division (returning a float), while the `//` operator was introduced for floor division.

2. **True Division**:
   - The term "true division" refers to the operation that converts operands to floats and performs division accordingly, ensuring that the result is always a floating-point number, even when both operands are integers.
   - This change was made to prevent confusion and errors that could arise from integer division, especially for users transitioning from other programming languages where division behaves differently.

## Naming Convention

- **Naming of `__truediv__`**:
  - The name `__truediv__` explicitly indicates that this method is responsible for true division. It helps clarify its purpose in the context of both true and floor division.
  - The use of "true" in the name emphasizes that this method implements the behavior expected from mathematical division, contrasting with the older integer division behavior.

## Example of True Division

Here’s an example demonstrating how `__truediv__` works:

```python
class Number:
    def __init__(self, value):
        self.value = value

    def __truediv__(self, other):
        return Number(self.value / other.value)

n1 = Number(5)
n2 = Number(2)
result = n1 / n2
print(result.value)  # Output: 2.5
```

### Comparison with Floor Division

To illustrate the difference between true division and floor division, consider the following:

```python
class Number:
    def __init__(self, value):
        self.value = value

    def __floordiv__(self, other):
        return Number(self.value // other.value)

n1 = Number(5)
n2 = Number(2)
true_div_result = n1 / n2          # Calls __truediv__
floor_div_result = n1 // n2         # Calls __floordiv__

print(true_div_result.value)  # Output: 2.5
print(floor_div_result.value)  # Output: 2
```

## Conclusion

Python allows extensive customization of how operators behave with user-defined classes through operator overloading. By implementing special methods like `__add__`, `__sub__`, and others for various operators, you can create intuitive and meaningful interactions between objects of your classes. This feature enhances code readability and usability while maintaining flexibility in how objects are manipulated.
In summary, `__truediv__` is used in Python 3 to clearly define the behavior of the `/` operator as true division, distinguishing it from the older `__div__` method used in Python 2. This change enhances clarity and reduces ambiguity regarding how division operations behave with different types of operands.
