# Mutable VS Immutable

## Mutable Data Types

**Mutable** objects are those whose values can be changed or modified after the object has been created. This means that you can alter the contents of these objects without creating a new object.

### Examples of Mutable Data Types

1. **Lists**: You can modify a list by adding, removing, or changing its elements.

   ```python
   my_list = [1, 2, 3]
   my_list[0] = 10  # Modifies the first element
   my_list.append(4)  # Adds a new element
   print(my_list)  # Output: [10, 2, 3, 4]
   ```

2. **Dictionaries**: You can change the values associated with keys or add new key-value pairs.

   ```python
   my_dict = {'a': 1, 'b': 2}
   my_dict['a'] = 3  # Changes the value of key 'a'
   my_dict['c'] = 4  # Adds a new key-value pair
   print(my_dict)  # Output: {'a': 3, 'b': 2, 'c': 4}
   ```

3. **Sets**: You can add or remove elements from a set.

   ```python
   my_set = {1, 2, 3}
   my_set.add(4)  # Adds an element
   my_set.remove(2)  # Removes an element
   print(my_set)  # Output: {1, 3, 4}
   ```

## Immutable Data Types

**Immutable** objects are those whose values cannot be changed after the object has been created. Any modification to an immutable object results in the creation of a new object rather than altering the original.

### Examples of Immutable Data Types

1. **Integers**: Once an integer is created, it cannot be changed.

   ```python
   x = 5
   x += 1  # This creates a new integer object and assigns it to x
   print(x)  # Output: 6
   ```

2. **Strings**: Strings cannot be modified in place; any operation that modifies a string creates a new string.

   ```python
   my_string = "Hello"
   my_string[0] = 'h'  # This will raise a TypeError
   my_string = "hello"  # This creates a new string object
   print(my_string)  # Output: hello
   ```

3. **Tuples**: Tuples cannot be altered once created; any attempt to modify them will raise an error.

   ```python
   my_tuple = (1, 2, 3)
   my_tuple[0] = 10  # This will raise a TypeError
   ```

## Summary of Differences

| Feature               | Mutable Data Types        | Immutable Data Types       |
|-----------------------|---------------------------|-----------------------------|
| Definition            | Can be changed after creation | Cannot be changed after creation |
| Examples              | Lists, Dictionaries, Sets | Integers, Strings, Tuples |
| Modification          | In-place modification      | Creates a new object on modification |
| Memory Efficiency     | More efficient for large data structures due to in-place changes | Less efficient due to creation of new objects |

Understanding the distinction between mutable and immutable types is crucial for effective programming in Python, as it affects how data is managed and manipulated within your applications.
