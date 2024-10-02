# Python Advanced Concepts

## Table of Contents

- [Python Advanced Concepts](#python-advanced-concepts)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Lesson Plan](#lesson-plan)
    - [01. Inheritance](#01-inheritance)
    - [02. Method Overriding](#02-method-overriding)
    - [03. Operator Overloading](#03-operator-overloading)
    - [04. `__init__` and `__del__` methods](#04-__init__-and-__del__-methods)
    - [05. Mutable and Immutable objects](#05-mutable-and-immutable-objects)
    - [06. Magic Methods](#06-magic-methods)
    - [07. Encapsulation and Access Specifiers](#07-encapsulation-and-access-specifiers)
  - [Getting Started](#getting-started)
  - [License](#license)
  - [Contributing](#contributing)
  - [Acknowledgments](#acknowledgments)

## Introduction

This repository contains notes and resources on advanced Python concepts. The topics covered in this repository include inheritance, method overriding, operator overloading, `__init__` and `__del__` methods, mutable and immutable objects, magic methods, and encapsulation and access specifiers.

## Lesson Plan

### 01. Inheritance

Read: [01_inheritence.md](01_inheritence.md)

Inheritance is a mechanism in object-oriented programming (OOP) that allows one class to inherit the properties and behavior of another class. The child class inherits all the attributes and methods of the parent class and can also add new attributes and methods or override the ones inherited from the parent class.

### 02. Method Overriding

Read: [02_method_overriding.md](02_method_overriding.md)

Method overriding is a feature in object-oriented programming that allows a subclass to provide a different implementation of a method that is already defined in its superclass. This is done to provide a more specific implementation of the method in the subclass.

### 03. Operator Overloading

Read: [03_operator_overloading.md](03_operator_overloading.md)

Operator overloading is a technique in object-oriented programming that allows developers to redefine the behavior of operators when working with user-defined objects. This enables objects of custom classes to be used with standard operators like `+`, `-`, `*`, etc.

### 04. `__init__` and `__del__` methods

Read: [04_init_and_del_methods.md](04_init_and_del_methods.md)

The `__init__` method is a special method in Python classes that is automatically called when an object of the class is instantiated. The `__del__` method is also a special method that is called when the object is about to be destroyed.

### 05. Mutable and Immutable objects

Read: [05_mutable_immutable.md](05_mutable_immutable.md)

In Python, some objects can be modified after they are created, while others cannot. Mutable objects are those that can be changed after creation, while immutable objects cannot.

### 06. Magic Methods

Read: [06_magic_methods.md](06_magic_methods.md)

Magic methods are special methods in Python classes that are automatically called by Python when certain operations are performed. These methods are surrounded by double underscores and are often used to implement operator overloading.

### 07. Encapsulation and Access Specifiers

Read: [07_encapsulation_and_access_specifiers.md](07_encapsulation_and_access_specifiers.md)

Encapsulation is a fundamental concept in object-oriented programming that involves bundling data and methods that manipulate that data within a single unit. Access specifiers are used to control access to the data and methods in a class.

## Getting Started

To get started with this repository, follow these steps:

1. Clone the repository to your local machine using `git clone`.
2. Install the required dependencies by running `pip install -r requirements.txt`.
3. Begin with the first lesson, `01_inheritence.md`, and work your way through the repository.

## License

This repository is licensed under the [MIT License](LICENSE).

## Contributing

Contributions are welcome! Please create a pull request with your proposed changes.

## Acknowledgments

This repository is based on [Python documentation](https://docs.python.org/3/) and other online resources.
