# The *args

The `*args` parameter allows a method to accept any number of positional arguments. The asterisk collects all extra positional arguments into a tuple.

Basic usage of `*args`:

```python
class Calculator:
def add_numbers(self, *args):
return sum(args)
calc = Calculator()
result1 = calc.add_numbers(1, 2, 3)
# 6
result2 = calc.add_numbers(10, 20, 30, 40, 50)
# 150
```

Combine regular parameters with `*args`:

```python
class Logger:
def log_message(self, level, *messages):
print(f"[{level}]", end=" ")
for message in messages:
print(message, end=" ")
print()logger = Logger()
logger.log_message("INFO", "User", "logged", "in")
```

Use `*args` in constructor methods:

```python
class Team:
def __init__(self, team_name, *players):
self.team_name = team_name
self.players = list(players)
team = Team("Warriors", "Alice", "Bob", "Charlie")
```

Unpack arguments when calling methods:

```python
numbers = [1, 2, 3, 4, 5]
result = calc.add_numbers(*numbers)
# Unpacks the list
```

Key Point: `*args` collects any number of positional arguments into a tuple. The name `args` is conventional but you can use any name after the asterisk.

# The **kwarg

The `**kwargs` parameter allows a method to accept any number of keyword arguments, collecting them into a dictionary:

```python
class Person:
def __init__(self, name, **kwargs):
self.name = name
self.details = kwargs
def show_info(self):
print(f"Name: {self.name}")
for key, value in self.details.items():
print(f"{key}: {value}")
person = Person("Alice", age=25, city="New York", job="Engineer")
```

Combine regular parameters, `*args`, and `**kwargs`:

```python
class Logger:
def log(self, level, *messages, **options):
timestamp = options.get('timestamp', False)
color = options.get('color', 'default')
if timestamp:
print("[2024-01-01 12:00:00]", end=" ")
print(f"[{level}]", end=" ")
for message in messages:
print(message, end=" ")logger = Logger()
logger.log("INFO", "User", "logged", "in", timestamp=True, color="green")
```

Unpack dictionaries when calling methods using `**`:

```python
settings = {"debug": True, "verbose": False, "log_level": "INFO"}
config = Config(**settings)
# Unpacks the dictionary
```

Access `**kwargs` values using dictionary methods:

```python
def get_setting(self, key, default=None):
return self.settings.get(key, default)
# Iterate through all kwargs
for key, value in self.settings.items():
print(f"{key} = {value}")
```

