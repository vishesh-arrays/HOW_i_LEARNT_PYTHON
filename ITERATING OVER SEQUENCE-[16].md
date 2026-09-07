# Iterating Over Elements

Iteration means going through elements one by one in a sequence. With lists, we can access each element systematically using different methods.

The most common way to iterate through a list is using a `for` loop:

```python
fruits = ["apple", "banana", "orange"]
for fruit in fruits:
print(fruit)
```

Output:

```python
apple
banana
orange
```

When iterating, you can also use the `len()` function to get the number of elements in a list, or to check the length of individual elements. For example, `len(fruits)` returns `3`, and `len("apple")` returns `5`:

```python
words = ["hi", "hello", "hey", "howdy"]
for word in words:
if len(word) > 3:
print(word)
```

Output:

```python
hello
howdy
```

# The Enumerate Function

The `enumerate()` function allows you to loop through a sequence (like a list, tuple, or string) while keeping track of the index position of each item.

without `enumerate()` we would access both the index and the value the following way:

```python
fruits = ["apple", "banana", "orange"]
for i in range(len(fruits)):
print(f"Index {i}: {fruits[i]}")
```

`enumerate()` is a more elegant way to get both index and value:

```python
fruits = ["apple", "banana", "orange"]
for index, fruit in enumerate(fruits):
print(f"Index {index}: {fruit}")
```

Both examples will output:

```python
Index 0: apple
Index 1: banana
Index 2: orange
```

