# Magic Methods Introduction

Magic methods (also called dunder methods) are special methods with double underscores at the beginning and end. Python calls them automatically in response to certain operations.

Here is an example of a class with magic methods:

```python
class Book:    
def __init__(self, title, author, pages):       
 self.title = title        
 self.author = author        
 self.pages = pages        
 def __str__(self):        
 return f"{self.title} by {self.author}"
```

The `__init__` method is called automatically when you create an object:

```python
my_book = Book("Python Programming", "John Smith", 350)
```

The `__str__` method is called automatically when you convert the object to a string:

```python
print(my_book)        # Calls __str__ automaticallyprint(str(my_book))   # Also calls __str__
```

Output:

```python
Python Programming by John SmithPython Programming by John Smith
```

Without `__str__`, printing would show the object's memory location:

```python
class SimpleBook:    def __init__(self, title):        self.title = titlesimple = SimpleBook("Test Book")print(simple)  # <__main__.SimpleBook object at 0x...>
```

Add another magic method for length:

```python
class Book:    def __init__(self, title, author, pages):        self.title = title        self.author = author        self.pages = pages        def __str__(self):        return f"{self.title} by {self.author}"        def __len__(self):        return self.pagesmy_book = Book("Python Programming", "John Smith", 350)print(len(my_book))   # Calls __len__ automatically
```

Output:

```python
350
```

Key Point: Magic methods start and end with double underscores (`__method__`) and are called automatically by Python. They allow your objects to work with built-in functions like `str()`, `len()`, and operators, making your classes more Pythonic and intuitive to use.

# Operator Overloading

Operator overloading allows your classes to work with Python's built-in operators (+, -, *, etc.) by implementing special magic methods.

Here is an example of a class with operator overloading:

```python
class Vector:    def __init__(self, x, y):        self.x = x        self.y = y        def __add__(self, other):        return Vector(self.x + other.x, self.y + other.y)        def __mul__(self, scalar):        return Vector(self.x * scalar, self.y * scalar)        def __str__(self):        return f"Vector({self.x}, {self.y})"
```

The `__add__` method defines what happens when you use the `+` operator:

```python
v1 = Vector(2, 3)v2 = Vector(5, 7)result = v1 + v2  # Calls v1.__add__(v2)print(result)
```

The `__mul__` method defines what happens when you use the `*` operator:

```python
v1 = Vector(2, 3)scaled = v1 * 3   # Calls v1.__mul__(3)print(scaled)
```

Output:

```python
Vector(7, 10)Vector(6, 9)
```

Add comparison operators:

```python
class Vector:    def __init__(self, x, y):        self.x = x        self.y = y        def __add__(self, other):        return Vector(self.x + other.x, self.y + other.y)        def __eq__(self, other):        return self.x == other.x and self.y == other.y        def __str__(self):        return f"Vector({self.x}, {self.y})"v1 = Vector(2, 3)v2 = Vector(2, 3)v3 = Vector(1, 1)print(v1 == v2)  # True - calls v1.__eq__(v2)print(v1 == v3)  # False
```

Key Point: Operator overloading uses magic methods like `__add__` (+), `__sub__` (-), `__mul__` (*), `__eq__` (==) to define how operators work with your objects. This makes your classes behave naturally with Python's built-in operators.

# Container Magic Methods

Container magic methods allow your classes to behave like built-in containers (lists, dictionaries, etc.). They enable indexing, length checking, and iteration on your custom objects.

Here is an example of a class with container magic methods:

```python
class CustomList:    
def __init__(self, items):        
self.items = items        
def __len__(self):        
return len(self.items)        
def __getitem__(self, index):       
 return self.items[index]        
 
def __setitem__(self, index, value):        
self.items[index] = value        
def __iter__(self):        
return iter(self.items)        def __contains__(self, item):        return item in self.items
```

The `__len__` method makes `len()` work:

```python
my_list = CustomList([1, 2, 3, 4])print(len(my_list))  # 4
```

The `__getitem__` method enables indexing for retrieval:

```python
print(my_list[2])    # 3print(my_list[0])    # 1
```

The `__setitem__` method enables indexing for assignment:

```python
my_list[1] = 10print(my_list[1])    # 10
```

The `__contains__` method makes the `in` operator work:

```python
print(3 in my_list)     # Trueprint(100 in my_list)   # False
```

The `__iter__` method enables iteration:

```python
for item in my_list:    print(item)
```

Output:

```python
43110TrueFalse11034
```

Key Point: Container magic methods like `__len__`, `__getitem__`, `__setitem__`, `__iter__`, and `__contains__` make your custom classes behave like built-in containers. This provides intuitive indexing, iteration, and membership testing for your objects.

**def __iter__(self):  
        return iter(self.items)  
      
   **def __contains__(self, item):  
        return item in self.items  
      
  **def append(self, item):  
        self.items.append(item)  
      
  **def pop(self):  
        return self.items.pop()  
      
  **def clear(self):  
        self.items.clear()