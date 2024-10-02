# Encapsulation and access specifiers

## What is Encapsulation in Python?

Encapsulation serves several purposes:

- **Data Protection**: It protects an object's internal state by restricting direct access to its attributes, thereby preventing unintended interference and misuse.
- **Interface Control**: It allows for a clear interface for interaction with the object while hiding the complex implementation details.
- **Modularity**: It promotes modularity by keeping related data and functions together, making the code easier to manage and understand.

In Python, encapsulation is implemented using access specifiers, which dictate how attributes and methods can be accessed from outside the class.

## Access Specifiers in Python

Python supports three main access specifiers:

| Access Modifier | Visibility                             | Naming Convention        | Description                                                                 |
|------------------|---------------------------------------|--------------------------|-----------------------------------------------------------------------------|
| Public           | Accessible Anywhere                   | No Prefix                | Members are accessible from anywhere, both inside and outside the class.   |
| Protected        | Accessible in Class and Subclasses    | Single Underscore Prefix | Members are accessible within the class and its subclasses.                |
| Private          | Accessible in Class Only               | Double Underscore Prefix  | Members are accessible only within the class where they are defined.       |

### 1. Public Members

Public members are accessible from any part of the program. By default, all members in Python are public unless specified otherwise.

**Example:**

```python
class PublicExample:
    def __init__(self):
        self.public_attribute = 27

    def public_method(self):
        return "This is a public method."

obj = PublicExample()
print(obj.public_attribute)  # Output: 27
print(obj.public_method())   # Output: This is a public method.
```

### 2. Protected Members

Protected members are intended to be accessible only within their own class and by subclasses. They are indicated by a single underscore prefix.

**Example:**

```python
class ProtectedExample:
    def __init__(self):
        self._protected_attribute = 27

    def _protected_method(self):
        return "This is a protected method."

obj = ProtectedExample()
print(obj._protected_attribute)  # Output: 27
print(obj._protected_method())   # Output: This is a protected method.
```

### 3. Private Members

Private members can only be accessed within the class they are defined in, indicated by a double underscore prefix. Direct access from outside the class will raise an `AttributeError`.

**Example:**

```python
class PrivateExample:
    def __init__(self):
        self.__private_attribute = 27

    def __private_method(self):
        return "This is a private method."

obj = PrivateExample()
# print(obj.__private_attribute)  # This will raise an AttributeError
# print(obj.__private_method())   # This will also raise an AttributeError
```

#### Accessing Private Members

While private members cannot be accessed directly, they can be accessed indirectly through public methods or by name mangling (using `_ClassName__attribute`).

**Example of Name Mangling:**

```python
class Example:
    def __init__(self):
        self.__private_variable = "I am private"

example = Example()
# Accessing private variable using name mangling
print(example._Example__private_variable)  # Output: I am private
```

## Conclusion

Encapsulation in Python enhances data security and integrity by controlling access to class members through public, protected, and private access specifiers. This helps maintain a clean interface while safeguarding the internal workings of a class, promoting better software design practices.

Public and protected methods in Python serve different purposes and are used in distinct scenarios, despite their similarities in being part of a class's interface.

## Differences Between Public and Protected Methods

- **Accessibility**:
  - **Public Methods**: These methods are accessible from anywhere in the code, both inside and outside the class. They form the primary interface for interacting with an object's functionality. By default, all methods in Python are public unless specified otherwise.
  - **Protected Methods**: These methods are intended to be accessed only within the class itself and by subclasses. They are marked with a single underscore prefix (e.g., `_method_name`). While they can be accessed from outside the class, it is discouraged as it goes against the intended encapsulation.

- **Intended Use**:
  - **Public Methods**: Used for general operations that should be available to any part of the program that has access to the object. They are part of the object's public API.
  - **Protected Methods**: Used for internal operations that should only be utilized by the class and its subclasses. They provide a way to share functionality with subclasses without exposing it to the outside world.

### Scenarios for Using Public and Protected Methods

- **When to Use Public Methods**:
  - **Interface Definition**: When you want to define methods that users of your class can call directly. For example, if you have a class representing a bank account, methods like `deposit()` and `withdraw()` would be public so that users can interact with their accounts.
  - **General Purpose Functionality**: Any method that needs to be accessed by external code or other classes should be public.

- **When to Use Protected Methods**:
  - **Subclassing**: When you want to allow subclasses to use certain methods but do not want those methods to be part of the public interface. For example, if you have a base class with some helper functions that should only be used by derived classes, you would mark those as protected.
  - **Internal Logic Sharing**: If a method is meant for internal calculations or processes that should not be exposed publicly but still need to be accessible by subclasses, it should be protected.

### Example Code

Here’s an illustrative example showing both public and protected methods:

```python
class BaseClass:
    def __init__(self):
        self.public_attribute = "I am public"
        self._protected_attribute = "I am protected"

    def public_method(self):
        return "This is a public method."

    def _protected_method(self):
        return "This is a protected method."

class DerivedClass(BaseClass):
    def access_protected(self):
        return self._protected_method()  # Accessing protected method

# Usage
base = BaseClass()
print(base.public_method())       # Accessible
print(base.public_attribute)      # Accessible
# print(base._protected_method()) # Not recommended, but accessible
# print(base._protected_attribute) # Not recommended, but accessible

derived = DerivedClass()
print(derived.access_protected()) # Accessing protected method through subclass
```

In this example:

- The `public_method` and `public_attribute` can be accessed freely from outside the class.
- The `_protected_method` and `_protected_attribute` are intended for use within `BaseClass` and its subclasses, demonstrating encapsulation while allowing subclass access.

## `@staticmethod` decorator

The `@staticmethod` decorator in Python is used to define a static method within a class. Unlike instance methods, static methods do not receive an implicit first argument (like `self` or `cls`). This means that static methods do not have access to instance-specific data or class-specific data, making them suitable for utility functions that logically belong to the class but do not require access to its attributes.

### Characteristics of Static Methods

- **No Implicit Parameters**: Static methods do not take `self` or `cls` as parameters. They are defined using the `@staticmethod` decorator.
- **Access to Class and Instance Attributes**: Static methods cannot access or modify class attributes or instance attributes directly.
- **Calling Convention**: They can be called using either the class name or an instance of the class.

### Example of a Static Method

Here’s a simple example demonstrating how to define and use a static method:

```python
class MathOperations:
    @staticmethod
    def add(x, y):
        return x + y

# Calling static method using class name
result = MathOperations.add(5, 3)
print(result)  # Output: 8

# Calling static method using an instance
math_instance = MathOperations()
print(math_instance.add(10, 20))  # Output: 30
```

### When to Use Static Methods

Static methods are particularly useful in the following scenarios:

- **Utility Functions**: When you have functions that perform operations related to the class but do not need to access any instance-specific or class-specific data. For example, mathematical calculations or formatting functions can be implemented as static methods.
  
- **Organizational Purposes**: When you want to group related functions within a class for better organization, even if those functions do not need access to the class's state.

## `@classmethod` decorator

The `@classmethod` decorator in Python is used to define a method that belongs to the class rather than any particular instance of the class. This means that the method can be called on the class itself, and it receives the class as its first argument, conventionally named `cls`. This allows the method to access class-level attributes and methods.

### Characteristics of Class Methods

- **First Parameter**: The first parameter of a class method is always `cls`, which refers to the class itself. This allows access to class attributes and other class methods.
- **Accessibility**: Class methods can be called on both the class itself and instances of the class.
- **Factory Methods**: Class methods are often used as factory methods that can create instances of the class.

### Example of a Class Method

Here’s a simple example demonstrating how to define and use a class method:

```python
class Student:
    name = 'unknown'  # Class attribute

    def __init__(self, age):
        self.age = age  # Instance attribute

    @classmethod
    def from_name(cls, name):
        # Factory method to create an instance from a name
        return cls(20)  # Returns an instance with age 20

    @classmethod
    def display_class_name(cls):
        print(f"Class Name: {cls.__name__}")

# Using the class method to create an instance
student_instance = Student.from_name('Alice')
print(student_instance.age)  # Output: 20

# Calling the class method directly from the class
Student.display_class_name()  # Output: Class Name: Student
```

### When to Use Class Methods

Class methods are particularly useful in various scenarios:

- **Factory Methods**: When you want to provide alternative constructors for your class. For example, you might want to create an instance based on different types of input (like strings or dictionaries).
  
- **Accessing Class State**: When you need a method that operates on class-level data rather than instance-level data. This is useful for maintaining state or behavior that is shared across all instances.

- **Inheritance**: Class methods can be overridden in subclasses, allowing you to modify their behavior while still accessing the same method signature.

### Comparison with Static Methods

To further clarify, here’s a comparison between `@classmethod` and `@staticmethod`:

| Feature               | @classmethod                              | @staticmethod                          |
|-----------------------|------------------------------------------|----------------------------------------|
| First Parameter        | `cls` (class itself)                    | None (no implicit parameter)          |
| Access to Instance Data| No                                       | No                                     |
| Access to Class Data   | Yes                                      | No                                     |
| Use Case              | Factory methods, accessing/modifying class state | Utility functions unrelated to instance/class state |

The `@staticmethod` decorator is a powerful feature in Python that allows developers to define methods that belong logically to a class but do not require access to its instance or class-level data. It promotes cleaner code organization and can be particularly useful for utility functions that enhance code readability and maintainability.

The `@classmethod` decorator is a powerful feature in Python that allows you to define methods that operate at the class level rather than on instances. This promotes cleaner code organization and provides flexibility in how classes can be instantiated and interacted with, especially in inheritance scenarios.
