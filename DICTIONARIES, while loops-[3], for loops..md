# DICTIONARIES!
1. Dictionaries are enclosed in curly brackets
2. Dictionaries contains duplicate keys
3. if you are making dictionaries, make sure that key is related to the word or anything you want to associate with.
4. Each key is unique
5. eg:
```   
months = {

    "Jan": "january",

    "Feb": "February",

    "Mar": "March",

}

print(months["Jan"])
```
7. so what this does is that, whenever we put some words, and associate it with anything else with colon it give that as an input.
8. There are many ways to get it like...
9. using  get(), it makes a default value for that key, if in case we can't find the key.
10. if the key is not found it says None
11. You can assign output to get(), that will it show when there is no key like that, by using comma after it.
---------------------------
# WHILE LOOOOPS
12. While loop is a structure in python which loops the code until it get false at a point.
13. while loop will execute the block of code until it gets false, so sometimes we need to add a limit otherwise it will run infinite times, it is never false.
14. eg:
```
#how while loops work

i=1

while i<=10:

    print(i)

    i+=1

print("done with loop ")
```
15. we can make a guessing game in which the player has to guess again and again until his guess becomes right.
16. eg:
```
# a guessing game

correct_guess= "dhurandar"

guess=""
guess_count = 0
guess_limit = 3
out_of_guess !=False
  

while guess != correct_guess and not(out_of_guess):
if guess_count < guess_limit:
    guess=input("enter guess : ")
    guess_count+=1
else:
    out_of_guess = True
if out_of_guess:
    print("out of guess you loss!")
print("you win!")
```
17. we can limit the number of times player can guess.
----------------------------
# FOR LOOPS
  18. we use "for" to make a loop
  19. it works well with lists and to find index and stuff..
  20. eg:
```
         friends = ["tony", "jimmy"]

for index in range (3,10):  here it won't take value 10

    print (index)
```
   21. you can use break to stop a loop immediately
   22. you can use continue in loop in loop to skip that particular part or sequence.
  
    
