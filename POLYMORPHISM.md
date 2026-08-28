# Method Overriding Revisited

Polymorphism means "many forms" and allows objects of different classes to respond differently to the same method call. Method overriding makes this possible.

Here is a parent class with a method:

```python
class Animal:    
def speak(self):        
return "Animal makes a sound"
```

Create child classes that override the same method:

```python
class Dog(Animal):    
def speak(self):        
return "Woof!"
class Cat(Animal):   
 def speak(self):       
  return "Meow!"
  class Cow(Animal):   
   def speak(self):        
   return "Moo!"
```

Each child class provides its own implementation of `speak()`.

Create a list of different animals:

```python
animals = [Dog(), Cat(), Cow(), Animal()]
```

Call the same method on all objects:

```python
for animal in animals:    
print(animal.speak())
```

Output:

```python
Woof!
Meow!
Moo!
Animal makes a sound
```

This is polymorphism in action - the same method call behaves differently based on the object's actual type.

You can also use polymorphism with functions:

```python
def make_animal_speak(animal):    
print(animal.speak())
dog = Dog()
cat = Cat()
make_animal_speak(dog)  # Woof!make_animal_speak(cat)  # Meow!
```

The function doesn't need to know what type of animal it receives - it just calls `speak()` and gets the right behavior.

Key Point: Polymorphism lets you treat different objects the same way through a common interface. Method overriding provides different implementations, while polymorphism lets you call them uniformly. This makes code more flexible and easier to extend.

# Duck Typing

Duck typing focuses on what an object can do, not what it is. If an object has the methods you need, you can use it - regardless of its class type.

Here are two unrelated classes with the same methods:

```python
class Duck:    
def swim(self):        
return "Duck swimming"        
def quack(self):        
return "Quack!"class Person:    
def swim(self):        
return "Person swimming"        
def quack(self):        
return "Person imitating a duck: Quack!"
```

Notice that Duck and Person don't inherit from the same parent class, but they both have `swim()` and `quack()` methods.

Create a function that works with any "duck-like" object:

```python
def make_it_swim_and_quack(duck_like_object):
print(duck_like_object.swim())    
print(duck_like_object.quack())
```

This function doesn't care about the object's type - it only cares that the object has the required methods.

Use the function with both classes:

```python
make_it_swim_and_quack(Duck())
make_it_swim_and_quack(Person())
```

Output:

```python
Duck swimmingQuack!Person swimmingPerson imitating a duck: Quack!
```

Add another "duck-like" class:

```python
class Robot:    
def swim(self):        
return "Robot swimming with propellers"        
def quack(self):        
return "Robot sound: BEEP BEEP!"
make_it_swim_and_quack(Robot())
```

Output:

```python
Robot swimming with propellersRobot sound: BEEP BEEP!
```

Key Point: Duck typing allows polymorphism without inheritance. If an object has the methods you need, you can use it. This makes Python code flexible and follows the principle "it's easier to ask forgiveness than permission."


# Abstract Classes and Methods

Abstract classes are classes that cannot be instantiated directly and contain abstract methods that must be implemented by subclasses.

**Think of it like a form:** An abstract class is like a mandatory form code where some fields are required (abstract methods) and some are optional (concrete methods). You can't submit the code itself - you must fill out all the required fields first. Similarly, you can't create instances of an abstract class until all abstract methods are implemented in a subclass.

Import the abc module to create abstract classes:

```python
from abc import ABC, abstractmethod
```

Create an abstract class with abstract methods:

```python
class Shape(ABC):    
@abstractmethod    
def area(self):        
pass        
@abstractmethod    
def perimeter(self):        
pass        
def describe(self):        
return "This is a shape"  
# Concrete method (has implementation)
```

The `@abstractmethod` decorator marks methods that **must** be implemented by subclasses - these are the "required fields" on your form. Regular methods like `describe()` can have implementations and are inherited as-is - these are the "pre-filled fields".

**Why use abstract classes?** They enforce a contract. If you create a `Shape` class, you're saying "every shape MUST be able to calculate its area and perimeter." This prevents bugs where you might forget to implement critical methods.

Try to create an instance of the abstract class:

```python
# This will cause an error:# shape = Shape()  # TypeError: Can't instantiate abstract class
```

This error is intentional - it's like trying to submit an empty form. Python is saying "You haven't filled in the required fields (area and perimeter methods) yet!"

Create a concrete subclass that implements all abstract methods:

```python
class Circle(Shape):    
def __init__(self, radius):       
 self.radius = radius        
 def area(self):        
 return 3.14 * self.radius ** 2        
 def perimeter(self):        
 return 2  3.14  
 self.radius
```

Now we've "filled in all the required fields" - we've implemented both `area()` and `perimeter()`. The Circle class is now a complete, concrete class that can be instantiated.

Now you can create instances of the concrete class:

```python
circle = Circle(5)
print(circle.area())
print(circle.perimeter())
print(circle.describe())  
# Inherited concrete method
```

Create another concrete subclass:

```python
class Rectangle(Shape):    
def __init__(self, width, height):        
self.width = width        
self.height = height        
def area(self):        
return self.width  self.height        
def perimeter(self):        
return 2  (self.width + self.height)rectangle = Rectangle(4, 6)
print(rectangle.area())
print(rectangle.perimeter())
```

Output:

```python
78.531.400000000000002This is a shape2420
```

Abstract classes define a code that subclasses must follow. Use `ABC` and `@abstractmethod` to create abstract classes. Subclasses must implement all abstract methods or they'll also be abstract. This ensures consistency and prevents incomplete implementations.


# Interface Design

An interface defines a contract that classes must follow. In Python, we create interfaces using abstract base classes where all methods are abstract.

Import the abc module:

```python
from abc import ABC, abstractmethod
```

Create an interface with abstract methods only:

```python
class Drawable(ABC):    
@abstractmethod    
def draw(self):       
 pass        
 @abstractmethod    
 def resize(self, width, height):       
  pass
```

All methods in an interface should be abstract - they define what implementing classes must do, not how to do it.

Implement the interface in a concrete class:

```python
class Circle(Drawable):    
def __init__(self, radius):        
self.radius = radius        
def draw(self):        
return "Drawing a circle"        
def resize(self, width, height):        
self.radius = min(width, height) / 2        
return f"Resized circle to radius {self.radius}"
```

Create another class that implements the same interface:

```python
class Rectangle(Drawable):    
def __init__(self, width, height):        
self.width = width        
self.height = height        
def draw(self):        
return "Drawing a rectangle"        
def resize(self, width, height):        
self.width = width        
self.height = height        
return f"Resized rectangle to {width}x{height}"
```

Use the interface polymorphically:

```python
shapes = [Circle(5), Rectangle(3, 4)]
for shape in shapes:    
print(shape.draw())    
print(shape.resize(10, 8))
```

Output:

```python
Drawing a circle
Resized circle to radius 4.0
Drawing a rectangle
Resized rectangle to 10x8
```

You can also use interfaces as type hints:

```python
def render_shape(drawable: Drawable):    
return drawable.draw()circle = Circle(3)
print(render_shape(circle))
```

Output:

```python
Drawing a circle
```

Key Point: Interfaces define what classes must do, not how they do it. Use abstract base classes with only abstract methods to create clear contracts that implementing classes must follow. This ensures consistent behavior across different implementations.