# The Map Function

The `map()` function takes two main things:

1. A function (which contains instructions for what to do)
2. A sequence of items (like a list, or any collection of elements)

It then applies that function to each item in your sequence, one by one, and gives you back all the results.

For example:

```python
def square(n):    
return n * numbers = [1, 2, 3, 4, 5]  # This is just a list of numberssquared_numbers = map(square, numbers)print(list(squared_numbers))# Output: [1, 4, 9, 16, 25]
```

What happened here:

- We have a list of numbers: [1, 2, 3, 4, 5]
- The `map()` function takes each number, one at a time
- It puts each number through our `square` function
- It collects all the results in order

You can think of it like an assembly line:

1. Number 1 goes in → square function makes it 1
2. Number 2 goes in → square function makes it 4
3. Number 3 goes in → square function makes it 9 And so on...

You can also use a lambda function instead of defining a separate function:

```python
numbers = [1, 2, 3, 4, 5]
squared_numbers = map(lambda n: n * n, numbers)
print(list(squared_numbers))# Output: [1, 4, 9, 16, 25]
```


The `map()` function works with any collection of items - not just numbers. It could be strings, or any other type of data you want to process in the same way.
# The Filter Function

The filter() function takes two main things:

1. A function (which contains instructions for checking each item)
2. A sequence of items (like a list, or any collection of elements)

It looks at each item in your sequence, one by one, and only keeps the ones that pass the function's test (when the function returns True).

For example:

```python
def is_even(n):    return n % 2 == 0numbers = [1, 2, 3, 4, 5, 6]  # This is just a list of numberseven_numbers = filter(is_even, numbers)print(list(even_numbers))# Output: [2, 4, 6]
```

What happened here:

- We have a list of numbers: [1, 2, 3, 4, 5, 6]
- The filter() function takes each number, one at a time
- It puts each number through our is_even function

- If the function returns True, it keeps that number
- If the function returns False, it drops that number

You can think of it like a strainer:

1. Number 1 goes in → `is_even` returns False → number dropped
2. Number 2 goes in → `is_even` returns True → number kept

3. Number 3 goes in → `is_even` returns False → number dropped And so on...

You can also use a quick, one-line function (called lambda) instead of defining a separate function:

```python
numbers = [1, 2, 3, 4, 5, 6]even_numbers = filter(lambda n: n % 2 == 0, numbers)print(list(even_numbers))# Output: [2, 4, 6]
```

The filter() function works with any collection of items - not just numbers. Here's an example with strings:

```python
words = ["apple", "banana", "cherry", "date"]long_words = filter(lambda word: len(word) > 5, words)print(list(long_words))# Output: ["banana", "cherry"]
```