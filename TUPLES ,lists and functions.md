#TUPLES, LIST, and Functions:
------------------------------
- tuple(): to create an empty tuple
- count(): to count the number of a specified item in a tuple
- index(): to find the index of a specified item in a tuple
- `+` operator: to join two or more tuples and to create a new tuple- \n: new line
- \t: Tab means(8 spaces)
- \\: Back slash
- \': Single quote (')
- \": Double quote (")
```
 print('I hope everyone is enjoying the Python Challenge.\nAre you ?') # line break
print('Days\tTopics\tExercises') # adding tab space or 4 spaces
print('Day 1\t5\t5')
print('Day 2\t6\t20')
print('Day 3\t5\t23')
print('Day 4\t1\t35')
print('This is a backslash  symbol (\\)') # To write a backslash
print('In every programming language it starts with \"Hello, World!\"') # to write a double quote inside a single quote
```
# output
-----------------------------
Days  Topics  Exercises
Day 1	5	    5
Day 2	6	    20
Day 3	5	    23
Day 4	1	    35
This is a backslash  symbol (\)
In every programming language it starts with "Hello, World!"
1. It is nothing but multiple lists at once
2. eg. coordinates=(4,5)
3. they are inevitable, they cannot be modified
4. even if you try to replace item or any change can give syntax error.
========
 5. def is a keyword used when we use it python thinks we are going to use a fxn, every fxn has its number.
 6. after using def whatever you will write there wil become a fxn and evething will lie in it, i.e when we use colon in it it shifts to same level as our fxn
 7. eg= def sayhi():
         hey     ..like that
8. even if you run, it won't work, Because when we write the code it is not executing as default. so we have to CALL A FXN
9. type fxn again without allignment 
10. if you print some thing above and below this fxn, it knows that he has apply fxn in btw the prints.
11. you put parameters inside the brackets, and use it for print fxn. like
12. eg.
```
14. def sayhi(name):
          print("Hello" + name)    
       so here, "name" is parameter
15.  you can add many parameters, by using commas 
16. then use + to add all strings and stuff
```
--------------------------

# RETURN STATEMENT
-return function allows python to return info to function 

 ----------------------
# IF STATEMENTS
help code to respond to the input and make decisions
use if code as we do usually, if you are printing something(with space) below the statement, it will execute it.
eg= i am going to work, if its cloudy i will get an umbrella with me OTHERWISE sunglasses...here "otherwise" is our ELSE statement and if is if.

1. NOTE = functions should not be blow each other like we do with adding parameter they should not gap horizontally and gap in vertically.
2. we can make multiple if and else fxns
by using and and or , after if like
if is_male or/and is_tall.......like that
# ELSE IF or elif = it comes btw if and else.
--------------------------
now what if you want "not abbreviate of it"?
we can use"not()" in it after using or and and
-if that statement is true it will turn it false.
-ELSE IF or ELIF, can be written multiple time to fulfill conditions in code:
```
is_male = False

is_tall=False

  if is_male and(is_tall):

    print("you are male or tall or both")

elif is_male and not(is_tall):

    print ("you are tall male")  

elif not(is_male) and (is_tall):

    print ("you are  maybe male but short")      

else:

    print("you are not men and not tall or not both ")
```
--------------------

ANOTHER WAY TO USE IF  by comparisons, by that we can do alot of things ...
it can take more than 3 parameters
we use COMPARISON OPERATORS like >= or <= or == or+=, -= etc
when we are comparing if, else or elif
-----------------------------

# MAKING A CALCULATOR
by using else, if, and elif we can see whether the user will use +,-,\ or *  and num1,num2 inputs
```
num1 = float(input("Enter first number:"))

op = input("Enter operation:")

num2 = float(input("Enter second number:"))
if op =="+":

    print(num1 + num2)

elif op == "-":

    print(num1-num2)

elif op == "*" :

    print(num1*num2)

elif op == "/" :

    print(num1/num2)    

else :

    print("invalid operation")
```
# LISTS:
15. use sq brackets to make a list with commas to sepreate things.
16. you can use numbers or index of element to show as output
1st element's index will be 0 in sq brackets
17. we can also access value of elements from back also by using -ve numbers
18. if you don't want 1st element  use 1: .
19. we can end selection in above point but 1:3 or 1:2 etc. it takes elements after 1 and 3, 1 and 2 respectively
- or you can change the elements by something else by assigning index number to other element.
----------------------
LIST FUNCTIONS :
20. extend() function = this can extend list further in it
just put all elemets you need in bracket above 
or you can make another list and  put it in bracket or u can use .append () fxn for same
21. `append()`, `extend()`, and `insert()` are Python list methods to add elements, differing by location and how they handle multiple items. `append()` adds a single item at the end, `extend()` unpacks an iterable to add multiple items at the end, and `insert()` adds a single item at a specific index.
22. use `remove()` to remove a item , or `clear()` to clean whole list
 you can also use `pop()` to remove last item frmo list (by default its target index is -1)
23. use `index("item")` to check whether it's in list or not, if yes itwill show its index otherwise no
24. use `count()` to see how many times that element is coming
sin list. (put item in brackets.
25. We can use `Sort()` To sort the list in Ascending order
 26. Make a new `copy()` To copy the list
    

























