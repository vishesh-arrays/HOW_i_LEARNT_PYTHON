Introduction to Decorators

Decorators are a way to modify or enhance functions and classes without changing their original code. They use the `@` symbol.

Here is an example of a simple decorator: 

```python
def my_decorator(func):    
def wrapper():        
print("Before function runs")        
func()        
print("After function runs")    
return wrapper
```

Apply the decorator using `@`:

```python
@my_decoratordef say_hello():    
print("Hello!")
```

Call the decorated function:

```python
say_hello()
```

Output:

```python
Before function runsHello!After function runs
```

The `@my_decorator` is equivalent to writing:

```python
def say_hello():    print("Hello!")say_hello = my_decorator(say_hello)
```

But the `@` syntax is much cleaner and easier to read.

Key Point: Decorators wrap around functions to add extra functionality without modifying the original function code

# Property Decorator

The `@property` decorator allows you to access methods like attributes, providing a clean way to get and set values.

Here is an example of a class using `@property`:

```python
class Circle:    def __init__(self, radius):        self._radius = radius        @property    def radius(self):        return self._radius        @property    def area(self):        return 3.14159 * self._radius ** 2
```

Create a circle and access properties:

```python
my_circle = Circle(5)
```

Access properties like regular attributes:

```python
print(my_circle.radius)print(my_circle.area)
```

Output:

```python
578.53975
```

Notice you don't use parentheses `()` when accessing properties - they look like attributes but run method code.

Add a setter to allow changing values:

```python
class Circle:    def __init__(self, radius):        self._radius = radius        @property    def radius(self):        return self._radius        @radius.setter    def radius(self, value):        if value > 0:            self._radius = value        else:            print("Radius must be positive!")
```

Now you can set the radius like an attribute:

```python
my_circle = Circle(5)my_circle.radius = 10  # Uses the setterprint(my_circle.radius)  # Uses the getter
```

Output:

```python
10
```

Key Point: `@property` makes methods look like attributes, while `@property_name.setter` allows you to control how values are assigned.


# Static Method Decorator

The `@staticmethod` decorator creates methods that don't need `self` or the class. They work like regular functions but belong to the class.

Here is an example of a class with static methods:

```python
class MathHelper:    @staticmethod    def add(a, b):        return a + b        @staticmethod    def is_even(number):        return number % 2 == 0
```

Call static methods using the class name:

```python
result = MathHelper.add(5, 3)print(result)check = MathHelper.is_even(10)print(check)
```

You can also call them from an object:

```python
helper = MathHelper()result2 = helper.add(2, 4)print(result2)
```

Output:

```python
8True6
```

Static methods don't access instance or class data:

```python
class Calculator:    brand = "Python Calc"        def __init__(self, owner):        self.owner = owner        @staticmethod    def multiply(x, y):        # Cannot access self.owner or Calculator.brand        return x * y
```

Key Point: Use `@staticmethod` when you need a function that's related to the class but doesn't need access to instance (`self`) or class data. No `self` parameter needed.


# Class Method Decorator

The `@classmethod` decorator creates methods that receive the class itself as the first parameter (`cls`) instead of an instance (`self`).

Here is an example of a class with class methods:

```python
class Student:    school_name = "Python Academy"    student_count = 0        def __init__(self, name):        self.name = name        Student.student_count += 1        @classmethod    def get_school_info(cls):        return f"School: {cls.school_name}, Students: {cls.student_count}"        @classmethod    def create_guest_student(cls):        return cls("Guest")
```

Call class methods using the class name:

```python
info = Student.get_school_info()print(info)
```

Create some students:

```python
alice = Student("Alice")bob = Student("Bob")updated_info = Student.get_school_info()print(updated_info)
```

Use class methods as alternative constructors:

```python
guest = Student.create_guest_student()print(guest.name)print(Student.get_school_info())
```

Output:

```python
School: Python Academy, Students: 0School: Python Academy, Students: 2GuestSchool: Python Academy, Students: 3
```

Class methods can also be called from instances:

```python
alice = Student("Alice")info_from_instance = alice.get_school_info()print(info_from_instance)
```

Output:

```python
School: Python Academy, Students: 1
```

Key Point: Use `@classmethod` when you need to access class attributes or create alternative ways to construct objects. The first parameter is `cls` (the class itself), not `self`.

# Instance vs Class Variables

Instance variables are unique to each object, while class variables are shared by all objects of the same class.

Here is an example of a class with both types of variables

```python
class Student:    # Class variable - shared by all instances    school = "Python High School"        def __init__(self, name, grade):        # Instance variables - unique to each student        self.name = name        self.grade = grade
```

Create student objects:

```python
alice = Student("Alice", "A")bob = Student("Bob", "B")
```

Access instance variables (unique to each object):

```python
print(alice.name)  # Aliceprint(bob.name)    # Bobprint(alice.grade) # Aprint(bob.grade)   # B
```

Access class variables (shared by all objects):

```python
print(alice.school)     # Python High Schoolprint(bob.school)       # Python High Schoolprint(Student.school)   # Python High School
```

Now change the class variable:

```python
Student.school = "Python Academy"
```

Check how the change affects all instances:

```python
print(alice.school)   # Python Academyprint(bob.school)     # Python Academy
```

Output:

```python
AliceBobABPython High SchoolPython High SchoolPython High SchoolPython AcademyPython Academy
```

You can also create instance variables after object creation:

```python
alice.age = 16  # This creates an instance variableprint(alice.age)  # 16# print(bob.age)  # This would cause an error - bob doesn't have age
```

Key Difference: Instance variables (created with `self.variable_name`) are unique to each object, while class variables (defined directly in the class) are shared by all objects. Changing a class variable affects all instances.


# Private Attributes

Private attributes use underscores to indicate that certain data should not be accessed directly from outside the class.

**Why do we need private attributes?** Imagine you have a bank account. You don't want anyone to directly change your balance - they should go through proper channels (deposit/withdraw methods) so the bank can validate the transaction, check for fraud, keep records, etc. Private attributes work the same way - they protect your data from being changed incorrectly.

Here is an example using single underscore (convention for "internal use"):

```python
class Person:    def __init__(self, name, age):        self._name = name    # "protected" - internal use        self._age = age      # "protected" - internal use
```

Single underscore attributes can still be accessed, but it's a signal not to:

```python
person = Person("Alice", 30)print(person._name)  # Works, but not recommended
```

Use double underscores for stronger privacy (name mangling):

```python
class Person:    def __init__(self, name, age):        self.__name = name   # "private" - gets name mangled        self.__age = age     # "private" - gets name mangled        def get_name(self):        return self.__name        def set_age(self, age):        if age >= 0:            self.__age = age        else:            print("Age must be positive!")
```

**Why use getter and setter methods?** They're like gatekeepers. Instead of letting anyone change `__age` directly (which could result in negative ages or other invalid data), we force them to use `set_age()` which validates the input first. This prevents bugs and ensures data integrity.

**The "extra code" has a purpose:**

- `get_name()` - Controlled access to read the name
- `set_age(age)` - Validates age before allowing changes (no negative ages!)
- Without these methods, someone could set `age = -100` and break your program

Use the accessor methods to interact with private attributes:

```python
person = Person("Bob", 25)print(person.get_name())  # Bobperson.set_age(30)        # Valid: age becomes 30person.set_age(-5)        # Invalid: Age must be positive! (age stays 30)
```

See the benefit? The `set_age()` method prevents invalid data. Without it, you could accidentally create a person with age -5, which makes no sense!

Double underscore attributes get "name mangled" but can still be accessed:

```python
person = Person("Charlie", 35)# This doesn't work:# print(person.__name)  # AttributeError# But this works (discouraged):print(person._Person__name)  # Charlie
```

**Real-world example - Why all this code?**

```python
class BankAccount:    def __init__(self, balance):        self.__balance = balance  # Private: can't be changed directly        def deposit(self, amount):        if amount > 0:            self.__balance += amount            return True        return False        def get_balance(self):        return self.__balance# Without private attributes:# account.__balance = -1000000  # Disaster! Negative balance allowed# With private attributes:account = BankAccount(100)account.deposit(50)           # Safe: validatedprint(account.get_balance())  # 150
```

The "extra code" (methods) protects your data from invalid changes. It's like having security guards instead of leaving your valuables unprotected.

Output:

```python
AliceBobAge must be positive!Charlie
```

Single underscore `_attribute` means "internal use only" by convention. Double underscore `__attribute` triggers name mangling for stronger privacy. Use getter/setter methods (accessor methods) to properly interact with private data and add validation. The "extra code" prevents bugs by ensuring data is always valid.

# Basic Inheritance

Inheritance allows a class to inherit attributes and methods from another class, creating a parent-child relationship.

Here is an example of a parent class:

```python
class Animal:    def __init__(self, name):        self.name = name        def info(self):        print(f"I am {self.name}, an animal")
```

Create a child class that inherits from the parent:

```python
class Dog(Animal):    pass  # Inherits everything from Animal
```

The syntax `class Dog(Animal):` means Dog inherits from Animal. Put the parent class name in parentheses.

Create objects from both classes:

```python
generic_animal = Animal("Creature")buddy = Dog("Buddy")
```

Use the inherited methods:

```python
generic_animal.info()buddy.info()
```

Output:

```python
I am Creature, an animalI am Buddy, an animal
```

Even though Dog doesn't define `__init__` or `info`, it automatically gets them from Animal.

You can add new methods to the child class:

```python
class Dog(Animal):    def bark(self):        print(f"{self.name} says Woof!")buddy = Dog("Buddy")buddy.info()  # Inherited methodbuddy.bark()  # New method
```

Output:

```python
I am Buddy, an animalBuddy says Woof!
```

Key Point: Child classes inherit all attributes and methods from their parent class. Use `class Child(Parent):` syntax to create inheritance. This helps you reuse code and create logical class hierarchies.

# The super() Function

The `super()` function allows a child class to call methods from its parent class. This lets you extend parent functionality rather than completely replace it.

Here is an example of using `super()` in the constructor:

```python
class Animal:    def __init__(self, name):        self.name = name        print(f"Animal created: {name}")class Dog(Animal):    def __init__(self, name, breed):        super().__init__(name)  # Call parent's __init__        self.breed = breed        print(f"Dog breed set: {breed}")
```

Create a dog object:

```python
buddy = Dog("Buddy", "Golden Retriever")print(f"Name: {buddy.name}, Breed: {buddy.breed}")
```

Output:

```python
Animal created: BuddyDog breed set: Golden RetrieverName: Buddy, Breed: Golden Retriever
```

Use `super()` to extend parent methods:

```python
class Animal:    def make_sound(self):        print("Generic animal sound")class Dog(Animal):    def make_sound(self):        super().make_sound()  # Call parent's method first        print("Woof!")        # Add dog-specific behavior
```

Call the extended method:

```python
buddy = Dog("Buddy", "Golden Retriever")buddy.make_sound()
```

Output:

```python
Generic animal soundWoof!
```

Without `super()`, you would lose the parent's functionality:

```python
class Cat(Animal):    def make_sound(self):        print("Meow!")  # Only cat sound, parent method ignoredcat = Cat("Whiskers")cat.make_sound()
```

Output:

```python
Meow!
```

Key Point: Use `super()` to call parent class methods from child classes. This allows you to extend functionality rather than completely replace it. Common uses include calling parent `__init__` methods and extending parent behavior.

# Method Overriding

Method overriding allows a child class to provide its own implementation of a method that already exists in the parent class.

Here is an example of a parent class with methods:

```python
class Animal:    def __init__(self, name):        self.name = name        def make_sound(self):        print("Some generic animal sound")        def info(self):        print(f"I am {self.name}")
```

Create a child class that overrides one method:

```python
class Dog(Animal):    def make_sound(self):        print("Woof! Woof!")  # Override the parent method
```

The `make_sound` method in Dog replaces the one from Animal, but `info` is still inherited unchanged.

Create instances and test the methods:

```python
animal = Animal("Generic Animal")dog = Dog("Buddy")
```

Call the overridden method:

```python
animal.make_sound()dog.make_sound()
```

Call the non-overridden method:

```python
animal.info()dog.info()
```

Output:

```python
Some generic animal soundWoof! Woof!I am Generic AnimalI am Buddy
```

You can override any inherited method:

```python
class Cat(Animal):    def make_sound(self):        print("Meow!")        def info(self):        print(f"I am {self.name}, a sneaky cat")cat = Cat("Whiskers")cat.make_sound()cat.info()
```

Output:

```python
Meow!I am Whiskers, a sneaky cat
```

Key Point: Method overriding lets child classes customize inherited behavior. Simply define a method with the same name in the child class. The child's version will be used instead of the parent's version.

# Multiple Inheritance

Multiple inheritance allows a class to inherit from more than one parent class, combining functionality from different sources.

Here are two parent classes:

```python
class Animal:    def __init__(self, name):        self.name = name        def eat(self):        return f"{self.name} is eating"class Flyable:    def fly(self):        return f"{self.name} is flying"
```

Create a child class that inherits from both parents:

```python
class Bird(Animal, Flyable):    def __init__(self, name, species):        super().__init__(name)  # Calls Animal's __init__        self.species = species        def sing(self):        return f"{self.name} is singing"
```

The syntax `class Bird(Animal, Flyable):` means Bird inherits from both Animal and Flyable.

Create a bird object and use methods from both parents:

```python
sparrow = Bird("Sparrow", "House sparrow")
```

Call methods from the first parent class:

```python
print(sparrow.eat())
```

Call methods from the second parent class:

```python
print(sparrow.fly())
```

Call the bird's own method:

```python
print(sparrow.sing())
```

Output:

```python
Sparrow is eatingSparrow is flyingSparrow is singing
```

You can check the inheritance order:

```python
print(Bird.__mro__)  # Method Resolution Order
```

This shows which parent gets checked first when looking for methods.

Key Point: Multiple inheritance uses `class Child(Parent1, Parent2):` syntax. The child class gets all methods from all parent classes. Python checks parents from left to right when looking for methods.

# Method Resolution Order

_Method Resolution Order (MRO) is the sequence Python uses to look for methods when multiple classes have the same method name.

Here is an example with multiple classes having the same method:

```python
class A:    def method(self):        return "Method from A"class B:    def method(self):        return "Method from B"class C(A, B):    pass
```

Check the MRO using `__mro__`:

```python
print(C.__mro__)
```

Output:

```python
(<class '__main__.C'>, <class '__main__.A'>, <class '__main__.B'>, <class 'object'>)
```

The `__mro__` attribute is a tuple that contains all classes in the resolution order. The first element (`__mro__[0]`) is always the class itself (C), followed by parent classes from left to right (A, then B), and finally the built-in object class.

Create an object and call the method:

```python
c = C()print(c.method())
```

Output:

```python
Method from A
```

Python found the method in class A first (at index 1 in the MRO), so it used that one.

Change the inheritance order to see the difference:

```python
class D(B, A):  # B comes before A now    passprint(D.__mro__)d = D()print(d.method())
```

Output:

```python
(<class '__main__.D'>, <class '__main__.B'>, <class '__main__.A'>, <class 'object'>)Method from B
```

Now Python finds B's method first because B comes before A in the inheritance list. You can access specific classes in the MRO using indexing - `D.__mro__[0]` is D itself, `D.__mro__[1]` is B, and `D.__mro__[2]` is A.

You can also use the `mro()` method:

```python
print(C.mro())
```

This gives the same result as `__mro__` but as a list.

Key Point: Python searches for methods in MRO order - the class itself first (index 0), then parent classes from left to right as listed in the class definition (indices 1, 2, etc.). The first method found gets used.



