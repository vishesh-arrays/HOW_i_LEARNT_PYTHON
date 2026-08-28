# External Files

External files let you organize your classes in separate Python files and import them into your main program.

Create a separate Python file called `my_class.py`

```python
class MyClass:
    def __init__(self, name):
            self.name = name        
            def greet(self):        
            return f"Hello, I'm {self.name}"
```


Import the class into your main file

```python
from my_class import MyClass
```

Create an instance and use it

```python
obj = MyClass("Alice")
print(obj.greet())
```

Output:

```python
Hello, I'm Alice
```

The `from my_class import MyClass` statement connects the `my_class.py` file to your program. The first `my_class` is the filename (without .py), and `MyClass` is the class name inside that file.


# Introduction to OOP

Object-Oriented Programming (OOP) organizes code around objects that contain data (attributes) and functions (methods).

Create a file called `car.py` with a class

```python
class Car:
pass  # placeholder that does nothing
```

Create another file called `driver.py` to use the class

```python
from car import Car
```

Create an object from the Car class

```python
my_car = Car()
```

Check the type of your object

```python
print(type(my_car))
```

Output:

```python
<class 'car.Car'>
```

This confirms you've successfully created an object from your Car class. In OOP, a class is like a blueprint, and an object is what you build from that blueprint.


# Classes vs Objects

Classes and objects serve different purposes. A class is a blueprint, while an object is what you build from that blueprint.

Here is an example of a class:

```python
class Dog:    # shared by all dogs
species = "Canis familiaris"
```

Now we can access the class attribute directly using `Dog.species` where `Dog` is the class name:

```python
print(f"Class species: {Dog.species}")# Class species: Canis familiaris
```

This accesses data from the class itself, not from any specific object.

Now lets explore how it works in objects. Create objects from the Dog class:

```python
dog1 = Dog()
dog2 = Dog()
```

Objects can have individual attributes that classes cannot:

```python
dog1.name = "Nicky"
dog1.breed = "Siberian Husky"
dog2.name = "Teemon" dog2.breed = "Shu'ali"
```

Compare what classes and objects can do:

```python
print(f"Object 1: {dog1.name} is a {dog1.breed}")
print(f"Object 2: {dog2.name} is a {dog2.breed}")
print(f"Both share class attribute: {Dog.species}")
```

Output:

```python
Object 1: Nicky is a Siberian Husky
Object 2: Teemon is a Shu'ali
Both share class attribute: Canis familiaris
```

**Key Difference:** The class `Dog` defines what all dogs have in common, while objects `dog1` and `dog2` represent specific, individual dogs with unique properties.

# The self Parameter

The self parameter refers to the instance of a class within methods. It allows you to access and modify attributes of the current object.

Here is an example of a class with methods using self:

```python
class Car:
def honk(self):
print("Beep beep!")
def describe(self):
print(f"I am a {self.color} {self.model}")
```

*The self parameter must always be the first parameter in method definitions. It tells the method which specific object is being used.*

Create a car object and add attributes:

```python
my_car = Car()
my_car.color = "Red"
my_car.model = "Sedan"
```

Now call the methods:

```python
my_car.honk()
my_car.describe()
```

Output:

```python
Beep beep!
I am a Red Sedan
```

*Notice that when calling `my_car.describe()`, you don't pass anything for self - Python automatically passes `my_car` as the self parameter.*

Here's what happens behind the scenes:

```python
# When you write this:my_car.describe()
# Python actually does this:Car.describe(my_car)
```

*The self parameter lets each object access its own data. Without self, methods wouldn't know which object's attributes to use.

_Key Point: Always include self as the first parameter in method definitions, but never pass it when calling methods - Python handles this automatically.

# Methods

Methods are functions that belong to a class. They define the behaviors or actions that objects can perform.

Here is an example of a class with methods:

```python
class Calculator:
def greet(self):
print("Hello! I'm a calculator.")
def add(self, a, b):
return a + b
def multiply(self, x, y):
result = x * y
print(f"{x} × {y} = {result}")
return result
```

Create a calculator object:

```python
my_calc = Calculator()
```

Call a method that doesn't need parameters:

```python
my_calc.greet()
```

Call methods with parameters:

```python
sum_result = my_calc.add(5, 3)
print(sum_result)
```

Call a method that both prints and returns a value:

```python
product = my_calc.multiply(4, 7)
```

Output:

```python
Hello! I'm a calculator.84 × 7 = 28
```

Methods can:

- Take parameters like `add(self, a, b)`
- Return values like `return a + b`
- Print output directly like `print("Hello!")`
- Do both printing and returning

Key Point: Methods define what your objects can do. Always include `self` as the first parameter, but don't pass it when calling the method.


# Attributes

Attributes are data or variables that belong to a class or its objects. They store information about the object's state.

There are two types of attributes: 

**Class attributes** - shared by all objects of the class:

```python
class Student:
school_name = "Python Academy"
# class attribute
```

**Instance attributes** - unique to each object:

```python
class Student:
school_name = "Python Academy"
def set_info(self, name, age):
self.name = name
# instance attribute
self.age = age
# instance attribute
```

Create student objects and set their individual data:

```python
student1 = Student()
student2 = Student()
student1.set_info("Alice", 20)
student2.set_info("Bob", 22)
```

Access instance attributes (unique to each object):

```python
print(student1.name)
# Aliceprint(student2.name)
# Bobprint(student1.age)     # 20
```

Access class attributes (same for all objects):

```python
print(student1.school_name)
# Python Academyprint(student2.school_name)
 # Python Academyprint(Student.school_name)
# Python Academy
```

Output:

```python
AliceBob20Python
AcademyPython
AcademyPython Academy
```

Key Difference: Class attributes are shared by all objects, while instance attributes are unique to each object. Use `self.attribute_name` for instance attributes and just `attribute_name` for class attributes.

# Constructor Method (__init__)

The `__init__` method is a special method that automatically runs when you create a new object. It initializes the object's attributes.

Here is an example of a class with a constructor:

```python
class Dog:
def __init__(self, name, breed):
self.name = name
self.breed = breed
```

The `__init__` method takes parameters and assigns them to instance attributes using `self`.

Create objects using the constructor:

```python
rex = Dog("Rex", "German Shepherd")
buddy = Dog("Buddy", "Golden Retriever")
```

When you call `Dog("Rex", "German Shepherd")`, Python automatically calls `__init__` and passes the arguments.

Access the attributes that were set by the constructor:

```python
print(rex.name
)print(rex.breed)
print(buddy.name)
print(buddy.breed)
```

Output:

```python
RexGerman
ShepherdBuddyGolden
Retriever
```

You can also have a constructor with default values:

```python
class Cat:
def __init__(self, name, age=1):
self.name = name
self.age = age# Create catsfluffy = Cat("Fluffy", 3)whiskers = Cat("Whiskers")
 # age defaults to 1print(f"{fluffy.name} is {fluffy.age} years old")
print(f"{whiskers.name} is {whiskers.age} years old")
```

Output:

```python
Fluffy is 3 years oldWhiskers is 1 years old
```

Key Point: The `__init__` method ensures every object is properly set up with its initial data when created. It saves you from manually setting attributes after object creation.
