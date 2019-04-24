---
title: Python 202
layout: post
weight: 10
hidden: true
---
​
**Course**: Data Science <br/>
**Mod**: 1 <br/>
**Topic**: Python 202 <br/>
**Amount of time**: 1.5 hours <br/>
**Author**: Alan Hong
​
***
​
## Lesson Summary:
​
#### Topic:
Python 202
#### Learn.co material:
- None
#### Prerequisite knowledge/ Prework:
- Python Fundamentals
#### Learning goals for this lesson:
Students will be able to:
- While Loops, Break and Continue
- Using Nested Loops
- Creating Functions
- Functions With Arguments
- User Input and Output in Python
- Mathematical Notation
- Measures of Central Tendency

#### Misconceptions:

#### Materials
- Filled Jupyter Notebook for you to refer to as you lecture
- Separation of Concerns for Python Functions: https://en.wikipedia.org/wiki/Separation_of_concerns

***

## Lesson Outline:

**Step**: While Loops, Break and Continue and Nested Loops <br/>
**Time**: 30 min

_Goal/Scenario and Demonstrate:_<br/>

Scenario: Today we are going to build upon the for loops of yesterday. 
Who has ever got to the cash register at costco, or whole foods, seen the total and asked "how did I spend that much?".
Today we have a grocery list of items and prices,  but we do not have infinite money (unfortunately), so we need to have a program that will look at our grocery list and help us manage our shopping and cost.


Activation:
Let's revisit what a for loop does. Here we have a list of items, and a separate list of costs.
We are going to write a loop to print each item, it's cost, and the total of our grocery list.

```
items = ['cheese', 'whole milk', 'kefir', 'tofu four-pack', 'kale', 'oranges', 'ham', 'ben & jerry's']
cost = [2.79, 3.42, 4.50, 12.00, 2.75, 3.64, 25.00, 5.29]
```

First, let's create a for-loop that prints each item in the list with "I need to buy:  " item.

```
for item in items:
   print("I need to buy : ", item)
```   

(let them figure out how to make the for loop the first way, then show them the following:)
 - Let's make that a little nicer looking:

```
print("I need to buy: ")
for item in items:
   print(" - [ ] ", item)
```

Okay, we want to work through a dictionary, so what's one way to convert those two lists to a dictionary?:

```
items_cost = dict(zip(items, cost))
print("I need to buy: ")
for key, value in items_cost.items():
  print("- [ ] ", key, ": for $", value)
```

So let's now add the total grocery bill at the end:

```
print("I need to buy: ")
total = 0
for key, value in items_cost.items():
  print("- [ ] ", key, ": for $", value)
  total = total + value
print("total cost: $", total)
```

- Does this look reasonable? 
- What if you only had $25? How can you build it out to stop adding items when the total is over $25?

### Introducing while loops

- What does a while loop look like in Python?
```
i = 1
while i < 6:
  print(i)
  i += 1
```
- Explain step by step how the above code is working and what you expect to see (expect to see 1,2,3,4,5 as output) before you run it in the notebook
- What is `break` and `continue`?
- Are they different? How?
- Run the following code:

```
i = 0
while i < 6:
  i += 1
  if i == 3:
    print("foo")
    continue
  print(i)

Output:
1
2
foo
4
5
6
```

- Go step by step how the above code is working.
- Now run this code:

```
i = 0
while i < 6:
  i += 1
  if i == 3:
    print("foo")
    break
  print(i)

Output:
1
2
foo
```
- Why is the output different?
- It stopped at `foo`, why?


- We can also include breaks in for-loops.
- What would we use to stop the for loop if the total reached $25?

```
print("I need to buy: ")
total = 0
for key, value in items_cost.items():
  print("- [ ] ", key, ": for $", value)
  total = total + value
  if total >= 25:
    break
print("total cost: $", total)
```

_Apply_ :

- What if we wanted to use `continue` and `break` to stop the program if an item costs more than $10 ?

```
print("I need to buy: ")
total = 0
for key, value in items_cost.items():
  print("- [ ] ", key, ": for $", value)
  if value >=10:
    print(key, " costs more than $10. Revise your list")
    print("Total cost below is before including ", key)
    break
  total = total + value
print("total cost: $", total)
```


### Nested Loops

_Demonstrate_ :
- Let's talk about nested loops next
- Write this code:

```
list = [1,2,3,4,5]

for x in list:
  print('loop1:', x)
  for y in list:
    print('loop2---', y)
```
- What do you expect to see? Why?
- Break it down what the loop is doing at each step.
- change some variables in the code to check for understanding from the group

- Here's a more complicated example, what is it doing?

```
i = 2
while(i < 100):
   j = 2
   while(j <= (i/j)):
      if not(i%j): break
      j = j + 1
   if (j > i/j) : print i, " is prime"
   i = i + 1

print "Good bye!"
```

_Apply:_ 

- Here is a more robust shopping list of nested dictionaries:

```
shopping_dict = {'Grocieries': {'ben & jerrys': 5.29, 'cheese': 2.79,'ham': 25.0, 'kale': 2.75,'kefir': 4.5,'oranges': 3.64,'tofu four-pack': 12.0,'whole milk': 3.42},
                 'House supplies': {'toilet paper pack': 16.50, 'clorox spray': 6.43, 'kleenex': 2.50,},
                 'Pet supplies': {'Taste of the Wild': 65.20, 'squeaky toy': 4.50, 'duck feet': 8.45}}
```
- write the nested for loops to print out each grocery list with its total

_Informal Assessment_:<br/>
"Quick check, how confident do we feel about loops and nested loops?"
- follow up with those students who do not feel confident

### Functions

**Step**: Creating Functions, Functions With Arguments, Input and Output <br/>
**Time**: 30 min

_Goal/Scenario and Demonstrate:_<br/>
- Why would we need to write functions?
- Separation of concerns (SoC), in computer science
- Modular code!
  - repeatable
  - doing things manually is the worst
  - standardization and human error reduction
- How do we write a function in python?

_Demonstrate:_
```
def sayHello():
  print("Hello!")
```
- How do we run it?

```
sayHello()
```
- Let's talk about arguments or parameters. Let's say we want to make this function more dynamic and print out whatever we want! How would we do that?
```
def shout(phrase):
  print(phrase + "!!!")

shout("oh hai")
```
- What if we don't pass in an argument? What happens?
- Maybe we can establish a default value for the argument in case it isn't passed in.

```
def shout(phrase = "oh hai"):
  print(phrase + "!!!")

shout()
shout("bye")
```

- What if we wanted to run a function, take it's output and put it in to another function?

```
def addOne(number):
  return number + 1

def timesFive(number):
  return number * 5

numberPlusOne = addOne(1)
answer = timesFive(numberPlusOne)
print(answer)
```

- What will the above code return?
_Apply_ : 

Adapt your shopping list nested for-loop to be wrapped in a function you could call on any shopping list of nested dictionaries. 

_Informal Assessment_:<br/>
"Quick check, how confident do we feel about functions and arguments?"
- follow up with those students who do not feel confident

**Step**: Mathematical Notation and Measures of Central Tendency <br/>
**Time**: 30 min

_Goal/Scenario and Demonstrate:_<br/>
- Measure of Central Tendency? That sounds really complicated! What the heck is it?
- Mean, Median, Mode
- What is a Mean? It's just an average. Take the sum of all the things and then divide them by the count.
- Median is the middle of the group when sorted from highest to lowest or lowest to highest.
- If there is an even number of things in the group, you take the average of the two things in the middle and that is your median.
- Mode is the value that is repeated the most in the group.

**Integration**

- adapt your function to do the following:
 - stop the nested loop if a grocery total goes over $30
 - print out the average cost of per item in your cart
 - print out the average cost per item in category
 
 Answer:
 
 ```
grand_tot = 0
grand_count = 0
for cat in list(shopping_dict.keys()):
    total = 0
    count = len(shopping_dict[cat].values())
    grand_count = grand_count + count
    print(cat+": ")
    for key, value in shopping_dict[cat].items():
        print("- [ ] ", key, " $", value)
        total = total + value
    average = total/count
    grand_tot=grand_tot + total
    print("average cost per {a}: ${p:8.2f}".format(a=cat,p=average))
grand_av = grand_tot/grand_count
print("average cost per item: ${p:8.2f}".format(p=grand_av))
 ```
 
 
 Just for average cost per item in category:
 
 ```
 for cat in list(shopping_dict.keys()):
     total = 0
     count = len(shopping_dict[cat].values())
     print(cat+": ")
     for key, value in shopping_dict[cat].items():
        print("- [ ] ", key, " $", value)
        total = total + value
     average = total/count
     print("average cost per {a}: ${p:8.2f}".format(a=cat,p=average))   
```

**Step**: Reflection <br/>
**Time**: 10 min <br/>
Ask the class and discuss as a group:
- What's an application of one of these new tools that you can think of for your own work? 
- What did you all find challenging about this content?
- What did you all find surprising?
- What did you all enjoy?
