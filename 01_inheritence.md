# python Inheritance

## What is Multiple Inheritance?

Multiple inheritance allows a class (child class) to inherit attributes and methods from more than one parent class. This can lead to more complex class hierarchies and increased code reuse.

### Syntax

The syntax for defining a class with multiple inheritance is as follows:

```python
class ChildClass(ParentClass1, ParentClass2):
    pass
```

## Example of Multiple Inheritance

Consider the following example involving vehicles and their characteristics:

```python
class Vehicle:
    def start(self):
        return "Vehicle started"

class Car(Vehicle):
    def drive(self):
        return "Car is driving"

class Boat(Vehicle):
    def sail(self):
        return "Boat is sailing"

class AmphibiousVehicle(Car, Boat):
    def amphibious_drive(self):
        return "Amphibious vehicle can drive on land or sail on water"

# Creating an instance of AmphibiousVehicle
amphibious = AmphibiousVehicle()
print(amphibious.start())  # Inherited from Vehicle
print(amphibious.drive())  # Inherited from Car
print(amphibious.sail())   # Inherited from Boat
print(amphibious.amphibious_drive())  # Own method
```

```bash
Vehicle started
Car is driving
Boat is sailing
Amphibious vehicle can drive on land or sail on water
```

In this example:

- `AmphibiousVehicle` inherits from both `Car` and `Boat`, allowing it to utilize methods from both classes.
- The `start` method is inherited from the `Vehicle` class, demonstrating how multiple inheritance can effectively combine functionalities.

## The Diamond Problem

The **Diamond Problem** occurs when a class inherits from two classes that have a common base class. This can lead to ambiguity about which method should be called. Here’s an example:

```python
class A:
    def greet(self):
        return "Hello from A"

class B(A):
    def greet(self):
        return "Hello from B"

class C(A):
    def greet(self):
        return "Hello from C"

class D(B, C):
    pass

# Creating an instance of D
d = D()
print(d.greet())
```

```bash
Hello from B
```

### Explanation

In this case:

- Class `D` inherits from both `B` and `C`, which in turn inherit from `A`.
- When calling the `greet` method on an instance of `D`, Python uses the **Method Resolution Order (MRO)** to determine which method to execute. The MRO prioritizes the first class listed in the inheritance declaration (`B`), hence it calls `greet()` from class `B`.

You can check the MRO using:

```python
print(D.mro())
```

```bash
[<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>]
```

This output shows the order in which Python looks for methods: first in `D`, then in `B`, followed by `C`, and finally in `A`.

## Conclusion

Multiple inheritance in Python provides a powerful way to create complex class hierarchies and promote code reuse. However, it requires careful design to avoid issues like method ambiguity as seen in the Diamond Problem. Understanding MRO is crucial for predicting how methods will be resolved in such scenarios.
