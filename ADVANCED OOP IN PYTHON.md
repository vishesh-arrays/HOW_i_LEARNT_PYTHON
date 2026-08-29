# Composition vs Inheritance

Object-oriented programming offers two main approaches for code reuse: inheritance ("is-a" relationship) and composition ("has-a" relationship).

Here is an example of inheritance creating an "is-a" relationship:

```python
class Animal:    
def __init__(self, name):        
self.name = name        
def eat(self):        
return f"{self.name} is eating"
class Dog(Animal):  
# Dog "is an" Animal    
def bark(self):        
return "Woof!"dog = Dog("Buddy")
print(dog.eat())  
 # Inherited methodprint(dog.bark())  # Own method
```

Here is an example of composition creating a "has-a" relationship:

```python
class Engine:    
def start(self):        
return "Engine started"        
def stop(self):        
return "Engine stopped"
class Car: 
 # Car "has an" Engine    
 def __init__(self):        
 self.engine = Engine() 
  # Composition        
  def start(self):       
   return self.engine.start()car = Car()
   print(car.start())  
   # Uses composed engine
```

Compare both approaches with a more complex example:

```python
# Inheritance approachclass Bird:
def move(self):
return "Flying"class Duck(Bird):
def quack(self):
return "Quack!"# Composition approach
class FlyBehavior:
 def move(self):
return "Flying"
class SwimBehavior:
def move(self):
return "Swimming"
class Duck:
def __init__(self):
self.fly_behavior = FlyBehavior()
self.swim_behavior = SwimBehavior()
def fly(self):
return self.fly_behavior.move()
def swim(self):
return self.swim_behavior.move()
def quack(self):
return "Quack!"
```

Test both approaches:

```python
# Inheritanceduck1 = Duck()
print(duck1.move())
# Flyingprint(duck1.quack())
# Quack!# Composition  duck2 = Duck()
print(duck2.fly())
# Flyingprint(duck2.swim())
# Swimmingprint(duck2.quack()) # Quack!
```

Output:

```python
Buddy is eating
Woof!
Engine started Flying
Quack!
Flying
Swimming
Quack!
```

Key differences:

**Inheritance:**

- Tight coupling between parent and child
- "Is-a" relationship
- Changes to parent affect all children
- Best for true hierarchical relationships

**Composition:**

- Loose coupling between objects
- "Has-a" relationship
- More flexible - can change behavior at runtime
- Easier to test and modify

Key Point: Use inheritance when you have a true "is-a" relationship. Use composition when you need flexibility and loose coupling. The principle "composition over inheritance" suggests favoring composition for most cases due to its flexibility and maintainability.


# Mixins

Mixins are a special kind of multiple inheritance used to "mix in" additional functionality to classes. They provide specific methods without being complete classes themselves.

Here is an example of a simple mixin:

```python
class JSONSerializableMixin:    
def to_json(self):        
import json        
return json.dumps(self.__dict__)
```

Let's break down what this mixin does:

- `self.__dict__` - This special attribute contains a dictionary of all the object's attributes and their values
- `json.dumps()` - This function converts the Python dictionary into a JSON-formatted string
- The mixin "mixes in" this JSON serialization functionality into any class that inherits from it

Now let's see it in action:

```python
class User(JSONSerializableMixin):
def __init__(self, name, email):        
self.name = name        
self.email = email
```

The mixin adds JSON functionality to any class that inherits from it:

```python
user = User("Alice", "alice@example.com")
print(user.to_json())
```

Output:

```python
{"name": "Alice", "email": "alice@example.com"}
```

The key insight: the User class now has the `to_json()` method without defining it directly. The mixin "mixed in" that functionality!

Create multiple mixins for different functionality:

```python
class PrintableMixin:    
def pretty_print(self):        
for key, value in self.__dict__.items():            
print(f"{key}: {value}")
class ComparableMixin:    
def __eq__(self, other):        
return self.__dict__ == other.__dict__
```

Each mixin accesses `self.__dict__` to work with the object's attributes, regardless of which class uses the mixin. This is the power of mixins - they provide reusable functionality that works with any class's attributes.

Combine multiple mixins in one class:

```python
class Product(JSONSerializableMixin, PrintableMixin, ComparableMixin):
def __init__(self, name, price):
self.name = name
self.price = priceproduct1 = Product("Laptop", 999)
product2 = Product("Laptop", 999)
```

Use all mixin functionalities:

```python
print(product1.to_json())
# From JSONSerializableMixin
product1.pretty_print()
# From PrintableMixin
print(product1 == product2)
# From ComparableMixin
```

Output:

```python
{"name": "Laptop", "price": 999}
name: Laptopprice: 999True
```

Key characteristics of mixins:

- Not meant to be instantiated on their own
- Provide specific, reusable functionality
- Don't usually have `__init__` methods
- Names often end with "Mixin" or "able"
- Can be combined with multiple inheritance
- Work with `self.__dict__` or other common object features to be flexible

Key Point: Mixins provide a way to share functionality across different class hierarchies without creating complex inheritance trees. They allow you to "mix in" specific capabilities like serialization, comparison, or printing to any class that needs them. This promotes code reuse and keeps classes focused on their primary responsibilities.

# Static and Class Methods

Besides regular instance methods, classes can have static methods and class methods that serve different purposes.

Here is an example of a static method:

```python
class MathHelper:
@staticmethod
def add(a, b):
return a + b
@staticmethod
def is_even(number):
return number % 2 == 0
```

==Static methods don't need `self` and work like regular functions. Call them directly from the class:

```python
result = MathHelper.add(5, 3)
print(result)check = MathHelper.is_even(10)
print(check)
```

Here is an example of a class method:

```python
class Person:
count = 0
# Class variable
def __init__(self, name):
self.name = name
Person.count += 1
@classmethod
def get_count(cls):
return cls.count
 @classmethod
def create_anonymous(cls):
return cls("Anonymous")
```

==Class methods receive the class itself (`cls`) as the first parameter:

```python
person1 = Person("Alice")
person2 = Person("Bob")
print(Person.get_count())  # 2
```

Use class methods as alternative constructors:

```python
anonymous = Person.create_anonymous()
print(anonymous.name)
# Anonymousprint(Person.get_count())  # 3
```

Compare all three method types in one class:

```python
class Calculator:
brand = "Python Calc"
def __init__(self, owner):
self.owner = owner
# Instance method - needs self, accesses instance data
def show_owner(self):
return f"Owned by {self.owner}"
# Class method - needs cls, accesses
class data
 @classmethod
def get_brand(cls):
return cls.brand
# Static method - needs neither, just a utility function
@staticmethod
def multiply(x, y):
return x * y
```

```python
calc = Calculator("Alice")
print(calc.show_owner())
# Owned by Aliceprint(Calculator.get_brand())
# Python Calcprint(Calculator.multiply(4, 5)) # 20
```

Output:

```python
8
True
2
Anonymous
3
Owned by Alice
Python Calc20
```

You can call class and static methods from instances too:

```python
calc = Calculator("Bob")
print(calc.get_brand())
# Python Calcprint(calc.multiply(2, 3))   # 6
```

Key Differences:

- **Instance methods**: Need `self`, access instance data
- **Class methods**: Need `cls`, access class data, good for alternative constructors
- **Static methods**: Need neither, just utility functions related to the class

Key Point: Use `@staticmethod` for utility functions that belong logically to the class but don't need class or instance data. Use `@classmethod` when you need access to the class itself, like for alternative constructors or accessing class variables.


# Class Decorators

Class decorators allow you to modify or enhance classes by wrapping them with another function. They work like function decorators but are applied to entire classes.

Here is a simple class without decoration:

```python
class Person:
def __init__(self, name):
self.name = name
def greet(self):
return f"Hello, my name is {self.name}"
```

Create a class decorator that adds a new method:

```python
def add_farewell(cls):
def farewell(self):
return f"Goodbye from {self.name}"
cls.farewell = farewell
 # Add the method to the class
return cls
```

Apply the decorator to a class using `@`:

```python
@add_farewell
class EnhancedPerson:
def __init__(self, name):
self.name = name
def greet(self):
return f"Hello, my name is {self.name}"
```

Now the class has both original and added methods:

```python
person = EnhancedPerson("Alice")
print(person.greet())
# Hello, my name is Alice
print(person.farewell())
# Goodbye from Alice
```

You can also **wrap an existing method** — storing the original so you can still call it inside the wrapper. This is useful when you want to add behaviour (like tracking or logging) around a method the class already has:

```python
def add_tracking(cls):
original_greet = cls.greet
# Store the original method
def tracked_greet(self):
print(f"greet was called")
# Extra behaviour before
return original_greet(self)
# Call the original method
cls.greet = tracked_greet
# Replace the method on the class
return cls@add_tracking
class TrackedPerson:
def __init__(self, name):
self.name = name
def greet(self):
return f"Hello, my name is {self.name}"
```

When you call `greet` now, the wrapper runs first, then delegates to the original:

```python
person = TrackedPerson("Alice")
print(person.greet())
# greet was called
# Hello, my name is Alice
```

The key steps for wrapping an existing method are:  
1. Save the original method: `original = cls.method`  
2. Define a new function that calls `original(self)` plus any extra logic.  
3. Assign the new function back to the class: `cls.method = new_function`  
4. Return the modified class.

Key Point: Class decorators take a class as input, modify or enhance it, and return the modified class. They can add methods, modify attributes, or wrap existing functionality. Use `@decorator_name` above the class definition to apply them. This provides a clean way to extend class functionality without inheritance.

# Context Managers

Context managers allow you to allocate and release resources precisely when needed. They ensure proper cleanup even if errors occur.

Here is the most common example using the `with` statement:

```python
with open('example.txt', 'w') as file:
file.write('Hello, world!')
# File is automatically closed here
```

The file is automatically closed after the block, even if an exception occurs.

Create your own context manager by implementing `__enter__` and `__exit__` methods:

```python
class MyContext:
def __enter__(self):
print("Entering the context")
return self
def __exit__(self, exc_type, exc_val, exc_tb):
print("Exiting the context")
return False  # Don't suppress exceptions
```

Use your custom context manager:

```python
with MyContext() as ctx:
print("Inside the context")
```

Output:

```python
Entering the context
Inside the context
Exiting the context
```

Create a more practical context manager for database connections:

```python
class DatabaseConnection:
def __init__(self, db_name):
self.db_name = db_name
self.connection = None
def __enter__(self):
print(f"Connecting to {self.db_name}")
self.connection = f"Connection to {self.db_name}"
return self.connection
def __exit__(self, exc_type, exc_val, exc_tb):
print(f"Closing connection to {self.db_name}")
self.connection = None
with DatabaseConnection("users_db") as conn:
print(f"Using {conn}")
print("Performing database operations...")
```

Handle exceptions in context managers:

```python
class SafeContext:
def __enter__(self):
print("Setting up resources")
return self
def __exit__(self, exc_type, exc_val, exc_tb):
print("Cleaning up resources")
if exc_type:
print(f"An exception occurred: {exc_val}")
return False  # Don't suppress the exceptionwith SafeContext():
 print("Working with resources")
# raise ValueError("Something went wrong")
# Uncomment to test
```

Output:

```python
Connecting to users_db
Using Connection to users_db
Performing database operations...
Closing connection to users_db
Setting up resources
Working with resources
Cleaning up resources
```

The `__exit__` method receives three parameters:

- `exc_type`: Exception type (or None)
- `exc_val`: Exception value (or None)
- `exc_tb`: Exception traceback (or None)

Key Point: Context managers use `__enter__` and `__exit__` methods to manage resources. The `with` statement automatically calls these methods, ensuring proper setup and cleanup. This is especially useful for files, database connections, and other resources that need guaranteed cleanup.
