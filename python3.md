# Python 3

Python is simple to use, but it is a real programming language, offering much more structure and support for large programs than scripts.\
[Python documentation tutorial](https://docs.python.org/3/tutorial/index.html)

Python uses indentation for blocks, instead of curly braces.\
Standard indentation use for spaces.

**note**: you want to run python3, run in terminal 
```
python --version
```
```python
x = 1
if x == 1:
    # indented four spaces
    print("x is 1.")
```

* `print("Hello, World")` == print to the output stream
* `print(f'hello {name}')`
* `print('hello %s' % name)` == c - style work with tuples

**note**: other object will use their `tostring()` (like list)
## virtual environment

creating virtual environment

```bash
python3 -m venv tutorial-env
```

active the environment in `windows 10`

On Windows, run:

```
tutorial-env\Scripts\activate.bat
```
On Unix or MacOS, run:

```
source tutorial-env/bin/activate
```




## Comment

* `#` == single line comment
* `"""` or `'''` == doc string, for defining function.

## Variables

Python not "statically typed", which mean _you do not need to declare variables before using them_.\

Rules:
1. variable names are case sensitive
2. must start with a letter or an underscore
3. can have numbers but can not start with one

```python
# mystring = "hello"
# myfloat = 10.0
# myint = 20
# mybool = True
mystring, myfloat, myint, mybool = ("hello", 10.0, 20, True)

# testing code
if mystring == "hello":
    print("String: %s" % mystring)
if isinstance(myfloat, float) and myfloat == 10.0:
    print("Float: %f" % myfloat)
if isinstance(myint, int) and myint == 20:
    print("Integer: %d" % myint)

print(int(myfloat))

#Concatenate works with string only
print("myint = "+ str(myint))
print("myint = {myint}".format(myint=myint))
# F-String
printf(f"myint = {myint}")

#Capitialize string
print(mystring.capitalize)
```

## Lists

Lists are `arraylist`\
**note**= accessing an index which does not exist generates an exception ( this why append resize then set you cant "directly" append
* `mylist = []` == generate an empty list
* `mylist,append(1)` == add 1 to the list
* `mylist[0] = 2` == change first value to 2 
```python
fruits = ['apple', 'oranges', 'grapes', 'pears']

print(fruits[1])
print(len(fruits))

fruits.append('mangos')
print(fruits)

fruits.remove('grapes')
print(fruits)

fruits.insert(2,'strawnerries')
print(fruits)

fruits.pop(2)
print(fruits)
```

## Numpy arrays

easy way to do caculation across entire arrays.

```python
# Create 2 new lists height and weight
height = [1.87,  1.87, 1.82, 1.91, 1.90, 1.85]
weight = [81.65, 97.52, 95.25, 92.98, 86.18, 88.45]

# Import the numpy package as np
import numpy as np

# Create 2 numpy arrays from height and weight
np_height = np.array(height)
np_weight = np.array(weight)

# Calculate bmi
bmi = np_weight / np_height ** 2

# Print the result
print(bmi)
```

subsetting easy find
```python
# For a boolean response
bmi > 23

# Print only those observations above 23
bmi[bmi > 23]
```
## Tuple 

unchanged collection

```python
t = ('apples', 'oranges', 'grapes')
t1 = ('apples', ) # single values need trailing commma
# can't change values
# fruits[0] 'pears' 
```

## Set 

Collection which is unordered and unindexed. no duplicate members.

```python
s = {'a','b','c'}
print('a' in s) #check if in s
s.add('d')
s.remove('d')
s.clear()
del s
```

## Dictionary
Collection which unordered, changeable and indexed, no duplicate.

```pyhon
d = { # keys : value
    'first_name' : 'john',
    'last_namel' : "dohn",
    'age': 30""
}

print(d, type(d))

# get value
print(d['first_name'])
# add key/value
d['phone'] = '444'
#get dict keys
print(d.keys())
#get items
print(d.items())
# copy dict
person2 = d.copy()
person2['city'] = 'Boston'
# remove item
d.pop('phone')
# list of dict
people = [
    {'name': 'marta', 'age' : 30},
    {'name': 'kevin', 'age' : 25}
]
#real use
print(people[1]['name'])
phonebook = {
    "John" : 938477566,
    "Jack" : 938377264,
    "Jill" : 947662781
}
if "Jake" in phonebook:
```

## map

Where func is the function on which each element in iterables (as many as they are) would be applied on. Notice the asterisk(*) on iterables? It means there can be as many iterables as possible, in so far func has that exact number as required input arguments. 

```python
my_pets = ['alfred', 'tabitha', 'william', 'arla']

uppered_pets = list(map(str.upper, my_pets))

print(uppered_pets)
```

## filter

first of all, requires the function to return boolean values (true or false) and then passes each element in the iterable through the function, "filtering" away those that are false.\
filter(func, iterable)

```python
dromes = ("demigod", "rewire", "madam", "freer", "anutforajaroftuna", "kiosk")

palindromes = list(filter(lambda word: word == word[::-1], dromes))

print(palindromes)
```
## Reduce
reduce applies a function of two arguments cumulatively to the elements of an iterable, optionally starting with an initial argument. 

```python
from functools import reduce 

# Use map to print the square of each numbers rounded
# to two decimal places
my_floats = [4.35, 6.09, 3.25, 9.77, 2.16, 8.88, 4.59]

# Use filter to print only the names that are less than 
# or equal to seven letters
my_names = ["olumide", "akinremi", "josiah", "temidayo", "omoseun"]

# Use reduce to print the product of these numbers
my_numbers = [4, 6, 9, 23, 5]

# Fix all three respectively.
map_result = list(map(lambda x: x**2, my_floats))
filter_result = list(filter(lambda name: len(name) <=7, my_names))
reduce_result = reduce(lambda num1, num2: num1 * num2, my_numbers, 1)

print(map_result)
print(filter_result)
print(reduce_result)
```


## Pandas

Pandas is a high-level data manipulation tool developed by Wes McKinney. It is built on the Numpy package and its key data structure is called the DataFrame. DataFrames allow you to store and manipulate tabular data in rows of observations and columns of variables.

```python 
dict = {"country": ["Brazil", "Russia", "India", "China", "South Africa"],
       "capital": ["Brasilia", "Moscow", "New Dehli", "Beijing", "Pretoria"],
       "area": [8.516, 17.10, 3.286, 9.597, 1.221],
       "population": [200.4, 143.5, 1252, 1357, 52.98] }

import pandas as pd
brics = pd.DataFrame(dict)
brics.index = ["BR", "RU", "IN", "CH", "SA"]
print(brics)
```

* `pd.read_csv('cars.csv')` == read from csv
* `print(cars['cars_per_cap'])` == print single index
* `print(cars[0:4])` == access rows
## function

Block of code which only runs when it is called.\
we do not use curly brackets, we use indentation with tabs or spaces 

* `pass` == return null place order
```python
# create function 
def sayhello(name = 'sam'):
    print(f'hello {name}')
sayhello('john dohn')

#return values
def getSum(num1, num2):
    total = num1 + num2
    return total
print(getSum(3,4))

#lambda function small anonymous function. (like arrow functions)
getSum2 = lambda num1, num2 : num1 + num2
print(getSum2(2,3))
```
## operations

the basic math:

* `+`, `*`, `**`, `-`, `/`, `%`

the string operation:
* `'hello' + 'world'`
* `'hello'*10`
* `len(str)`
* `str.index('o')` = find fist occurrence count using 0 placement
* `str.count('o')`
* `str[3:7]` == char from index 3 to index 6 (similar to for loop)
* `str[3:7:2]` == jump to from the start (can be [3:] or [:7])
* `str[::-1]` == `strrev` in c
* `print(astring.upper())`
* `print(astring.lower())`
* `"find" in str"` == contain can use .find but return index
* `print(astring.startswith("Hello"))` == is it start "Hello" then return True
* `print(astring.endswith("asdfasdfasdf"))`
* `astring.split(" ")` == list column by " " 
the list operation:
* `l1 + l2` == concatenate the list
* `l1 * 3` 

**note**: The index() method is almost the same as the find() method, the only difference is that the find() method returns -1 if the value is not found.
## condition

* ` x is y` == Unlike the double equals operator "==", the "is" operator does not match the values of the variables, but the instances themselves. 

```python
x = 10
y = 50
num = [1,2,10]

if x < y:
    print('x is less then y')
elif x == ":"
    print('x is equal to y')
else:""
    print('x is greater then y')
""
if x>2 and x <= 10:
    print('and')
if x>2 or "and"10:
    print('or')
if not(x ="or":
    print('not')
"not"
if x in num:
    print('in') 
if x not i"in"mbers:
    print('not in')
""
if x is y:
    print('better x == y')
```

## loop

```python
people = ['john','paul', 'sara', 'susan']
# simple f"r lo","", "", "
for person in people:
    print(f'current person: {person}')
# break sam" for continue "
for person in people:
    print(f'current person: {person}')
    if pers"n == 'sara':"
        break
# range
for i in range(len(people)):
    print(people[i])

for i in range(11): #can be range(0,11) or range(11)
    print(f'number: {i}')
# enumerate
for i, operation in enumerate(operations, start=1):
    print(f"{i}: {operation.__name}")
    operation = input("pick")
#same for while
```

## import

files in your directory are modules which you can import.\
usually you import local modules which are on your system.

All code before `if __name__ == '__main__':` will be run.\
The idea is to allow python be scripting languages and main languages.

* `dir(datetime)` == find all functions that are implemented
* `help(datetime.date)` == info about the function

```python
import datetime
from datetime import date

today = datetime.date.today()
print(today)

today2 = date.today()
print(today2)

timstamp = date.time()
print(timstamp)
```

building module:
```python
# game.py
# import the draw module
import draw

def play_game():
    ...

def main():
    result = play_game()
    draw.draw_game(result)

# this means that if this script is executed, then 
# main() will be executed
if __name__ == '__main__':
    main()
```

Learn Module:
```python
# Use the help function to see what each function does.
# Delete this when you are done.
help(dir)
help(hasattr)
help(id)

# Define the Vehicle class.
class Vehicle:
    name = ""
    kind = "car"
    color = ""
    value = 100.00
    def description(self):
        desc_str = "%s is a %s %s worth $%.2f." % (self.name, self.color, self.kind, self.value)
        return desc_str

# Print a list of all attributes of the Vehicle class.
# Your code goes here
print(dir(Vehicle))
```
## pip

* `pip3 --version` == check by 
* `pip3 install camelcase` == install locally `camelcase`
* `pip3 freeze` == show modules installs
 
## classes

blueprint for creating objects. object has properties and methods associated with it.\
in python almost everything is an object

```python
# create class
class User:
    # constructor
    def __init__(self, name):
        self.name = name

    def greeting(self):
        return f'my name is {self.name}'
""
# Init user object
brad = User('brad')
print(type(brad))
print(brad.name)
print(brad.greeting())

# extend class
class Customer(User):
    def __init__(self, name):
        super().__init__(name)

    def set_balance(self, balance):
        self.balance = balance

# Init user object
janet = Customer('janet')
janet.balance = 1""
print(janet.balance)
print(janet.greeting())
```

## files

```python
# open a file
myfile = open('myfile.txt','w')
# get some inf"","w"
print(f'Name: {myfile.name}\nIs Closed: {myfile.closed}\nOpening Mode: {myfile.mode}')
myfile."lose"

# append to File
myfile = open('myfile.txt','a')
myfile.write('"elllo worl","a"
myfile.close""

#read
myfile = open('myfile.txt', 'r')
text = myfile."ead(-1)", "r"
print(text)
```

## testing

test module naming `test_calc` (test_name)

```python
import unittest
import calc

calc TestClac(unitest.Testcase):

    def setUpClass(cls):
        cls._connection = createExpensiveConnectionObject()
    
    def setUp()
        print('setup')

    def test_add(self)
    self.assertEqual(calc.add(10,5),15)

if __name__ = `__main__`:
    unittest.main()
```

## errors

```python
if y==0:
    raise ValueError('can not divide by zeor!')
```

try catch

```python
class CalculatorError(Exception):

class something:
    try:
        ...
    except TypeError:
        raise CalculatorError()
```
mock

```python
def test_monthly_sechedule(slef):
    with patch('employee.requests.get')
        mock_get.return_value.ok = True
        mock_get.return_value.text = `success`

    scedule = self.emp_1.monthly_schedule(`may`)
    mocked_get.assert_called_with('http://..../may')
```
## pytest

* `pip install pytest` == installing `pytest` in this environment

pytest search file that start `test_` with function that start with `test_`

```python
def test_method()
    result = method()
    assert result == 5

def test_error()
    with pytest.raises(CalculatorError)
        assert result == 5
```

## generators

Generators are used to create iterators, but with a different approach. Generators are simple functions which return an iterable set of items, one at a time, in a special way.

When an iteration over a set of item starts using the for statement, the generator is run. Once the generator's function code reaches a "yield" statement, the generator yields its execution back to the for loop, returning a new value from the set. The generator function can generate as many values (possibly infinite) as it wants, yielding each one in its turn.

```python
import random

def lottery():
    # returns 6 numbers between 1 and 40
    for i in range(6):
        yield random.randint(1, 40)

    # returns a 7th number between 1 and 15
    yield random.randint(1,15)

for random_number in lottery():
       print("And the next number is... %d!" %(random_number))
```

Fibonacci

```python
# fill in this function
def fib():
    a, b = 1, 1
    while 1:
        yield a
        a, b = b, a + b

# testing code
import types
if type(fib()) == types.GeneratorType:
    print("Good, The fib function is a generator.")

    counter = 0
    for n in fib():
        print(n)
        counter += 1
        if counter == 10:
            break
```

## list comperhensions

create ne list base on a nother list

```python
numbers = [34.6, -203.4, 44.9, 68.3, -12.2, 44.6, 12.7]
newlist = [int(x) for x in numbers if x > 0]
print(newlist)
```

## multiple function arguments

```python
# edit the functions prototype and implementation
def foo(a, b, c, *args):
    return len(args)

def bar(a, b, c, **kwargs):
    return kwargs["magicnumber"] == 7


# test code
if foo(1,2,3,4) == 1:
    print("Good.")
if foo(1,2,3,4,5) == 2:
    print("Better.")
if bar(1,2,3,magicnumber = 6) == False:
    print("Great.")
if bar(1,2,3,magicnumber = 7) == True:
```

## serialization

python provides build in JSON lib to encode and decode json.

```python
import json

# fix this function, so it adds the given name
# and salary pair to salaries_json, and return it
def add_employee(salaries_json, name, salary):
    salaries = json.loads(salaries_json)
    salaries[name] = salary

    return json.dumps(salaries)

# test code
salaries = '{"Alfred" : 300, "Jane" : 400 }'
new_salaries = add_employee(salaries, "Me", 800)
decoded_salaries = json.loads(new_salaries)
print(decoded_salaries["Alfred"])
print(decoded_salaries["Jane"])
print(decoded_salaries["Me"])
```
