# Method Overriding

Method overriding occurs when a subclass provides a specific implementation of a method that is already defined in its superclass. This allows the subclass to modify or extend the behavior of that method. Here’s a simple example:

```python
class Parent:
    def show(self):
        return "Inside Parent"

class Child(Parent):
    def show(self):
        return "Inside Child"

# Usage
child_instance = Child()
print(child_instance.show())  # Output: Inside Child
```

In this example, the `Child` class overrides the `show` method of the `Parent` class.

## Method Overloading

While Python does not support method overloading natively (i.e., defining multiple methods with the same name but different parameters), there are ways to simulate it.

### Alternative Approaches to Simulate Method Overloading

1. **Using Default Parameters**:
   You can define a single method with default parameter values to handle different numbers of arguments.

   ```python
   class Example:
       def add(self, a=0, b=0, c=0):
           return a + b + c

   obj = Example()
   print(obj.add(10, 20, 30))  # Output: 60
   print(obj.add(10, 20))      # Output: 30
   ```

2. **Using Variable-Length Arguments**:
   You can use `*args` to accept a variable number of arguments.

   ```python
   class Example:
       def add(self, *args):
           return sum(args)

   obj = Example()
   print(obj.add(10, 20, 30))  # Output: 60
   print(obj.add(10, 20))      # Output: 30
   ```

3. **Using Third-Party Libraries**:
   The `multipledispatch` library can be used to achieve true method overloading by allowing multiple methods with the same name but different signatures.

   ```python
   from multipledispatch import dispatch

   class Example:
       @dispatch(int, int)
       def add(self, a, b):
           return a + b

       @dispatch(int, int, int)
       def add(self, a, b, c):
           return a + b + c

   obj = Example()
   print(obj.add(10, 20))      # Output: 30
   print(obj.add(10, 20, 30))  # Output: 60
   ```

### Conclusion

In summary:

- **Method Overriding** is fully supported in Python and allows subclasses to provide specific implementations of inherited methods.
- **Method Overloading**, as traditionally defined in other languages, is not supported directly in Python. However, it can be simulated using default parameters, variable-length arguments, or third-party libraries like `multipledispatch`.
