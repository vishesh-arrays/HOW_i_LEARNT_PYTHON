# Public, Protected, Private Mem

Python has three levels of access control for class members: public, protected, and private. These control how attributes and methods can be accessed.

Here is an example of a class with all three access levels:

```python
class BankAccount:    
def __init__(self, owner, balance, account_id):        
self.owner = owner           
# Public - accessible anywhere        
self._balance = balance     
 # Protected - internal use        
 self.__account_id = account_id  
 # Private class only        
 def deposit(self, amount):      
  # Public method        
  self._balance += amount        
  def _calculate_interest(self):   
  # Protected method        
  return self._balance * 0.02       
   def __validate_transaction(self, amount): 
    # Private method        
    return amount > 0 and amount <= self._balance
```

Access public members from anywhere:

```python
account = BankAccount("Alice", 1000, "12345")
print(account.owner)        
# Aliceaccount.deposit(500)        
# Works fine
```

Access protected members (single underscore - convention only):

```python
print(account._balance)     
# 1500 works but not recommended
result = account._calculate_interest()  
# Works but not recommendedprint
(result)               # 30.0
```

Try to access private members (double underscore - name mangled):

```python
# This won't work:
# print(account.__account_id)  
# AttributeError
# But this works (name mangling):print(account._BankAccount__account_id)  # 12345
```

Create a subclass to show protected vs private access:

```python
class SavingsAccount(BankAccount):    
def show_balance(self):        
return self._balance        
# Protected - accessible in subclass        
def show_id(self):        
# return self.__account_id  
# This won't work - private       
 return "Cannot access private member"
```

```python
savings = SavingsAccount("Bob", 2000, "67890")
print(savings.show_balance()) 
 # 2000print(savings.show_id())       
 # Cannot access private member
```

Output:

```python
Alice30.0123452000
Cannot access private member
```

Key Point: Public members have no prefix and are accessible anywhere. Protected members use single underscore (`_`) and should only be used within the class hierarchy. Private members use double underscore (`__`) and are name-mangled for stronger privacy. Python's access control is convention-based, not strictly enforced.

# Access Modifiers

Access modifiers control the visibility of class attributes and methods. Python uses naming conventions rather than keywords for access control.

Here is an example of public access (no prefix):

```python
class Person:    
def __init__(self):        
self.name = "Coddy"      
# Public attribute            
def greet(self):             
# Public method        
return f"Hello, I'm {self.name}"
```

Access public members from anywhere:

```python
person = Person()
print(person.name)           
# Coddyprint(person.greet())        
# Hello, I'm Coddy
```

Here is an example of protected access (single underscore):

```python
class Employee:    
def __init__(self):        
self._salary = 50000     
# Protected attribute        
def _calculate_bonus(self):  
# Protected method        
return self._salary * 0.1    
def show_bonus(self):        
return self._calculate_bonus() 
 # OK to use within class
```

Access protected members (works but not recommended):

```python
employee = Employee()
print(employee._salary)      
# 50000 - works but discouraged
print(employee.show_bonus()) 
# 5000.0 - proper way
```

Here is an example of private access (double underscore):

```python
class User:    def __init__(self):        self.__password = "secure123"   # Private attribute            def __encrypt(self, data):          # Private method        return f"Encrypted: {data}"            def verify(self, input_password):        # Private members accessible inside the class        return input_password == self.__password
```

Use private members correctly:

```python
user = User()
print(user.verify("secure123"))  # True - using public method
# print(user.__password)         # AttributeError - cannot access directly
```

Output:

```python
CoddyHello, I'm Coddy500005000.0True
```

Key Point: Python access modifiers are naming conventions: no prefix = public (accessible anywhere), single underscore = protected (internal use), double underscore = private (class only). These help establish clear boundaries and prevent accidental misuse of class internals.


# Information Hiding

Information hiding restricts direct access to object components, requiring all interactions to occur through well-defined interfaces. This protects internal data from unauthorized access.

Here is an example of a class with different levels of information hiding:

```python
class BankAccount:    
def __init__(self, owner, initial_balance):        
self.owner = owner                    
# Public -can be accessed directly        
self._balance = initial_balance       
# Protected - internal use        
self.__account_number = "ACC123456"  
 # Private - hidden from outside
```

Add methods that provide controlled access to hidden data:

```python
class BankAccount:    
def __init__(self, owner, initial_balance):        
self.owner = owner        
self._balance = initial_balance        
self.__account_number = "ACC123456"            
def deposit(self, amount):        
if amount > 0:            
self._balance += amount            
return True        
return False        
def withdraw(self, amount):        
if amount > 0 and amount <= self._balance:            
self._balance -= amount            
return True        
return False        
def get_balance(self):        
return self._balance        
def get_account_info(self):       
 # Safe way to show partial private data        
 return f"Owner: {self.owner}, Account: ***{self.__account_number[-4:]}"
```

Use the class through its public interface:

```python
account = BankAccount("Alice", 1000)
```

Access public data directly:

```python
print(account.owner)  # Alice - public access OK
```

Use controlled methods for protected data:

```python
print(account.get_balance())  
# 1000 - controlled accessaccount.deposit(500)
print(account.get_balance())  # 1500 - balance changed safely
```

Try to access hidden data:

```python
print(account.get_account_info())  # Owner: Alice, Account: ***3456

# print(account.__account_number)  # AttributeError - hidden
```

The private attribute is name-mangled but still technically accessible:

```python
# This works but violates information hiding:
print(account._BankAccount__account_number)  # ACC123456
```

Output:

```python
Alice10001500Owner: Alice, Account: ***3456ACC123456
```

Key Point: Information hiding protects internal data by making it private or protected, then providing controlled access through public methods. This prevents direct manipulation of sensitive data and ensures data integrity through validation in the access methods.

# Property Decorators Advanced

Advanced property decorators provide more sophisticated control over attribute access, including computed properties, deleters, and full property management.

Here is an example of computed properties that derive values from other attributes:

```python
class Rectangle:    
def __init__(self, width, height):        
self.width = width        
self.height = height       
 @property    
 def area(self):        
 return self.width * self.height        
 @property    
 def perimeter(self):        
 return 2 * (self.width + self.height)
```

Use computed properties like regular attributes:

```python
rect = Rectangle(5, 3)
print(rect.area)      
# 15 - calculated automatically
print(rect.perimeter) # 16 - calculated automatically
```

Create a property with getter, setter, and deleter:

```python
class Temperature:    
def __init__(self):        
self._temp = 0        
@property    
def temperature(self):        
return self._temp        
@temperature.setter    
def temperature(self, value):       
 if value < -273.15:            
 raise ValueError("Temperature below absolute zero!")        
 self._temp = value        
 @temperature.deleter    
 def temperature(self):        
 print("Resetting temperature to 0")        
 self._temp = 0
```

Use the full property functionality:

```python
temp = Temperature()
```

Use the setter with validation:

```python
temp.temperature = 25
print(temp.temperature) 
 # 25# temp.temperature = -300  
 # Would raise ValueError
```

Use the deleter:

```python
del temp.temperature
print(temp.temperature)  # 0
```

Create a more complex example with a game score:

```python
class Player:    
def __init__(self, name):        
self.name = name        
self._score = 0        
self._level = 1        
@property    
def score(self):       
 return self._score       
  @score.setter    
  def score(self, value):        
  if value >= 0:            
  self._score = value            
  self._level = (value // 1000) + 1       
   else:            
   raise ValueError("Score cannot be negative")        
   @score.deleter    def score(self):        
   print(f"Resetting {self.name}'s progress")        
   self._score = 0        
   self._level = 1        
   @property    
   def level(self):        
   return self._levelplayer = Player("Alice")player.score = 2500
   print(f"Score: {player.score}, Level: {player.level}") 
    # Score: 2500, Level: 3del player.score
    print(f"Score: {player.score}, Level: {player.level}")  
    # Score: 0, Level: 1
```

Output:

```python
151625
Resetting temperature to 00
Score: 2500, Level: 3
Resetting Alice's progress
Score: 0, Level: 1
```

Key Point: Advanced property decorators allow computed properties (calculated from other data), property deletion with `@property.deleter`, and full control over getting, setting, and deleting attributes. This creates intuitive interfaces while maintaining strong data validation and encapsulation.

