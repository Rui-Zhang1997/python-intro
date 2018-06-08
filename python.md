# Introduction
Python is a language designed for code conciseness and rapid prototyping. It is widely used in the mathematical and analytical fields due to its simplicity, flexibility, and extensibility as well as providing many libraries created for that purpose. However, it also forms the core stack of many of today's tech companies, such as every major tech company, reddit, dropbox amongst others. Therefore, it is very useful to be able to code in the language, both because it is used by many companies but also because you can stand up personal work extremely quickly.
# Things To Keep Note
1. Python is whitespace dependent, so unlike C or Java where whitespace does not matter, it does in Python. Instead of using braces to denote which blocks of code belong together indents are used. This helps to keep a uniform code structure. Therefore, if there are any inconsistencies in the examples, it is because I do not know how to use Markdown properly. 

# Types
Python has types:

1. int - integers. Non-decimal values
2. float - floats. Decimal values
3. str - strings. Can be denoted by single or double quotes. For large multi-line strings one uses triple single or double quotes.
4. object - All objects inherit from the base 'object' class.
5. dict - A standard key-value data structure like a dictionary or hashmap. The keys and values do not have to be of one type. The value can be of any type but the key must be hashable (e.g. the key cannot be another dict). Unordered.
6. list - Similar to an arraylist in java. Similar to an array except it is not fixed size. A list can hold values of multiple types and can hold other lists
7. tuple - Similar to a list and can be accessed like a list but cannot be modified (i.e. no value can be added, modified, or removed.
8. set - Each element can only appear once. Unordered.
9. function - A defined function
10. class - A defined class

# Syntax
### Variables
All variables are created and initialized at once, unlike in C or Java where you can do
```python
int a
```
In Python, one must do
```python
<variable> = <value>
```
If a variable should not have an initial value, then one can assign it `None`.
### Functions
The basic syntax of a Python function follows standard function declaration formats i.e.
```python
def <function name>(<parameters, if any>):
````
followed by code. All code must be indented by one and only one indent following a function declaration. There is no return type.

Unli
### Conditions
There is a single conditional in Python, which is the {\em if...elif...else}. Unlike other languages, there is no switch. The syntax
```python
if (not) <condition> (and|or) <condition> .... :
```
Python does not use operators such as `!`, `&`, and `||` to denote negation, and, or but instead uses `not`, `and`,  `or`, respectively. Using the symbols results in a `SyntaxError`. There is also another operator which is `in`, allowing one to test for membership within a collection. For example,
```python
'hello' in 'hello world'

# or
1 in [1, 2, 3, 4]

# or
'apples' not in ['pears', 'lemons', 'grapes']
```
#### Ternary Operators
Python does not have a ternary operator (`<condition> ? <execute if true> : <execute if false>`) and this was a design choice.
Instead, one can use a modified if else:
```python
<value if condition true> if <condition> else <value if condition false

# e.g.
a = 10
b = a-1 if a == 10 else a+1
```
### Loops
Python has loops, `while` and `for`, which has the following syntax.
```python
for <variables> in <collection>:
	<code>
    
while <conditions>:
	<code>
```
#### For Loops
Note that the for loop is not your standard for loop, which has the form 
```
for (initialization; test; increment) {
	<code>
}
```
. If one needs to iterate over an integer range, such as from 0 to 9, then one can iterate over that range in Python like so:
```python
for <variable> in range(10):
	<code>
```
Which will iterate from 0 to 10. The syntax for the range function is as follows:
```python
range(end) # goes from 0 to end-1
range(start, end) # goes from start to end-1
range(start, end, step) # goes from start to end-1 where
						# each iteration increments the variable by step
```
The last one allows us to step backwards, such as from 10 to 0 one would do `range(10, -1, -1)`, as range stops at the stop value. This is very useful when iterating over a list, dict, sets, and tuple. For lists, sets, and tuples, iteration is the same:
```python
for <variable> in <some list, set, or tuple>:
	<code>

# e.g.
lst = [1, 23, 44, 3]
for i in lst:
	print(i)

# output
1
23
44
3
 ```
The above assigns `<variable>` a value of an element in the list or tuple. If one also needs the index, then one would do

```python
for <index-variable>, <value-variable> in enumerate(<some-list-set-or-tuple>):
	<code>

# e.g.
lst = [1, 23, 44, 3]
for i, v in enumerate(lst):
	print(i,v)

# output is
0 1
1 23
2 44
3 3
 ```
 
which will assign the index of each element to the first variable and the value to the second variable.

For dictionaries, it is very similar:
```python
for <key> in <some-dict>:
	<code>
 ```
Which will assign each key of the dictionary to the `key` variable. For both key-value,
```python
for <key>, <value> in <some-dict>.items():
	<code>
 ```
Will assign key to the first variable and the value to the second.
### While
While is very similar to whiles in other languages.
```python
while <conditions>:
	<code>
```
### Notes
Unlike other languages, `for` and `while` also takes an `else` clause, which will execute if the loop completes. This is useful if one is searching for something in a list and wants different code to execute if it finds what it is looking for in the list and do something else if one is not found. For example, let us say we are looking for a name. If a name is found, then one would stop searching but if it is not found, then the loop completes and the else would execute. This is cleaner than using a flag, for example
```python
# without using for...else...
found = 0
for name in names:
	if name == 'John':
    	<code>
        found = 1
        break
if found == 0:
	<name not found code>
<other code>

# using for...else...
for name in names:
	if name == 'John':
    	<code>
        break
else:
	<name not found code>
<other code>
```
### Classes
Python is an object-oriented language, meaning that it supports classes. Class declarations are as follows:
```python
class <class name>:
	<functions>
    
# if inheriting from other classes
class <class name>(<classes inherited from>):
	<functions>
```
The constructor for a class is a special function called the \_\_init\_\_ function, which is empty by default.

All instance functions are defined as follows:
```python
def <function name>(<self-reference-parameter>, <parameters>):
	<code>
```
The first parameter of an instance function is the *self parameter*, which is traditionally called "self" but can be called anything one wants, is used to reference instance functions and variables (e.g. `self.variable` or `self.function()`). If one is making a static function (or static method, as it is so called in Python), then the first parameter is not the *self parameter* and alos must append the @classmethod decorator to the line above, e.g.
```python
@classmethod
def <function-name>(<parameters>):
	<code<
```
Creating an instance of a class is just like any other OOP language:
```python
class A:
	def __init__(self, value):
    	self.value = value
    def increment(self):
    	self.value += 1
    def get_increment(self):
    	self.increment()
        return self.value
        
a = A(10) # initializes variable `a` to equal an instance of class A where
		  # a.value is 110
```
Please note that Python has no concept of public, private, or protected methods and attributes. That is because Python operates under the idea that "we are all consenting adults". This means that whoever is using a class knows what they are doing and therefore nothing is hidden and any misuse of the attributes or functions is the fault of the client code. Typically, any function starting with an underscore is a function that is not usually called or should not be called.
### Notes
Java does not allow inheriting from multiple classes as that runs into the diamond problem, which is if a class C inherits from classes A and B and they each have a foo() function inside with the same method signature, which one do you run? Python solves this by using the order of inheritance so if one did class C(A,B) it would check A for foo() then B for foo().

# Programming Constructs
### Lambdas
Sometimes there is something that can be done by a function but is only one expression, or one is in a situation where there is a function that requires another function as an argument but the function being passed in is only a single expression (such as in cases for `map` or `filter`). At this point, one would use a lambda, which can be thought of as an anonymous function:
```python
lambda <variables>: <expression>

# e.g.
add_one = lambda v: v + 1
c = add_one(10) # c == 11

# e.g.
get_remainder = lambda a, b: a % b
c = get_remainder(5, 3) # c == 2
```
The value of `expression` is returned from the function (if it does not return anything, for example if it is a print statement, it returns None). Lambdas can also be assigned to variables as well.
### Comprehensions
One of Python's most powerful tools is its ability to perform comprehensions. These are very useful when one wishes to perform an operation on a list to produce another list. For example, let us make a list of the squares of numbers from 0 to 9.
```c
// in C:
int squares[10];
int i;
for (i = 0; i < 10; i++) {
	squares[i] = i * i;
}
```
```java
// in Java
int[] squares = new int[10];
for (int i = 0; i < 10; i++) {
	squares[i] = i * i;
}
```
```python
# in python without list comprehension
squares = []
for i in range(10):
	squares.append(i * i)
	
# in python with list comprehensions
squares = [i * i for i in range(10)]
```
While a trivial example, it is meant to demonstrate the power of comprehensions. They allow programmers to shrink code that would take multiple lines into a single expression. The most basic form of the list comprehension is:
```python
[<expression> for <variable> in <collection>]

# e.g.
[foo(i) for i in [1, 2, 3, 4, 5]]

# or
[(k,v) for k,v in dictionary.items()]
```
One can also do some basic filtering in these comprehensions
```python
a = [<expression> for <variable> in <collection> if <condition>]

# e.g.
a = [i * i for i in range(10) if i % 2 == 0]
	# ^^^ generate list of squares for positive numbers only
```
Note: one does not need to have the variable in the expression:
```python
[0 for i in range(10)] # makes [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
```
One can also nest comprehensions
```python
sent = "This is a sentence with words"
sent_long_words_only = [word for word in [word.lower() \
	for word in sent.split(' ')] if len(word) > 4]
```
However, this is not only for lists. This can be used for dicts as well:
```python
{<key>: <value> for <variables> in <collection>}

# e.g.
some_dict = {k: foo(k) for k in a_list}
```
### Built-in Functions
Python provided a lot of useful built-in functions as well.

**map** The `map` function is very useful in taking a collection and apply a given function to it. This is very similar to a list comprehension however map is *lazy* unlike comprehensions which are *eager*. Sometimes, we might not need an entire list at once but small chunks or even a single element of it, do some work on it, and go on to the next small segment. With a list comprehension, all the data is always stored in memory which, if we are dealing with a lot of data, may not be the best thing for us to do. With a map, only when we need that particular segment of the list is the data actually processed. For example, if we have a list of names and want to pull the accounts associated with the names and send some notices, if there is a lot of data per individual then it would be very expensive memory-wise to store all of that in a list. Instead, with a map, we can pull data for a single name, process it, and then go on to the next one, which allows us to save space as we are storing a single user's data at a time. This also comes with the drawback that we cannot reference a previous value in the map as it can be thought of as removed from memory. However, if one uses a map and then wants to convert it to a list, then one can just apply the `list()` function to the map and it will generate the list. It is defined as follows:
```python
map(<function name or lambda>, collection)

# e.g.
def send_notices(username):
	data = get_large_data(username)
    return send_notices_if_condition(data)
    
names = ['John Doe', 'Jane Hathaway', ... ]
notices_sent = map(send_notices, names)

# or
squares = map(lambda i: i * i, range(10))
```
**filter** The `filter` function does what it sounds like it does: filters through a collection based on a specific criteria. The function passed as the first parameter must given must return a boolean.
```python
filter(<test function>, <collection>)

# e.g.
evens = filter(lambda i: i % 2 == 0, range(100))
```
filter is *lazy* as well.
**sorted** The `sorted` function sorts a list. However, it is destructive, as in it modifies the original list. Given a simple list like an array of integers it will sort it how one expects it to (unlike Javascript). However, if it is a list of tuples and one wishes to sort by the second element, then one needs to give a key function, which specifies which element to sort by
```python
a = [1, 11, 3, 4]
sorted(a)
# a is now [1, 3, 4, 11]

# with "key function"
sorted(<collection>, <key function>)

# e.g.
a = [(3,2), (1,1), (4, -1)]
sorted(a) # result: [(1,1), (3,2), (4,-1)]
sorted(a, lambda k: k[1]) # result: [(4,-1), (1,1), (3,2)]

# reverse the sorted list
a = [4, 2, 3, 1]
sorted(a, reversed=True) # result: [4, 3, 2, 1]
```
**reversed** Reverse an existing ordered collection (like a list). However, it is also *lazy*

**zip** Occasionally, one may receive two or more lists or tuples and we wish to associate all the first elements, the second elements, etc. (for example, if given a list of account holders and checkings and savings accounts), we could use a for-loop
```python
account_holders = [...list of names...]
checkings = [...values...]
savings = [...values...]
accounts = []
for i in range(len(accounts)):
	accounts.append((account_holders[i], savings[i], checkings[i]))
```
This way works, but we can also do the last three lines in a single line:
```python
account_holders = [...list of names...]
checkings = [...values...]
savings = [...values...]
accounts = list(zip(account_holders, savings, checkings)) # lazy -> eager
```
**len** Gets the length of a collection

**dict, list, tuple, set** Can be used to convert from one collection to another. `dict` can convert a list of two-tuples into a dict:
```python
a = [(1,2), (3,4)]
dict(a) # {1: 2, 3: 4}
```
`list` Can be used to convert any of the listed collections and any lazy function into a list. If applied to a dictionary, then it will only use the keys. For both (key, value), use `list(d.items())` where `d` is a dictionary.
`tuple` will also do the same as list but will turn it into a tuple.
**open** Used to open a file. This returns an `io.TextWrapper` object, which can be used to read the contents of the file.
```python
f = open('<file path>', '<permissions>')
f = open('<file path>', 'r') # read only
f = open('<file path>', 'w') # write only
f = open('<file path>', 'w+') # opens for read and write. File
							  # created is created if does not exist else 
							  # it is truncated (all contents deleted)
f = open('<file path>', 'r+') # open for read and write and move cursor to start
f = open('<file path>', 'a') # open for writing, moves cursor to EOF
f = open('<file path>', 'a+') # open for read and write, move cursor to EOF
f.read() # gets all data from the file
f.readline() # gets a single line from the file
f.readlines() # gets all lines from the file and stores it into an array
			  # where each element is a line
f.seek(<offset>, <reference>) # goes to offset bytes from reference:
							  # 0 - start of file
							  # 1 - current position
							  # 2 - end of file
f.close() # closes the object
```
Keeping the file open (i.e. `not calling f.close()`) is not a good idea and, depending on the system, the file may not be released. However, sometimes one might forgot, so to prevent it, one can use the `with...as...` construct:
```python
with open('<file path>', '<permissions>') as <variable>:
	<code>
# file is closed
```
**dir** List all methods and attributes in a particular class or object.

**super** In a class that inherits from other classes, `super()` can be used to reference the superclass.

**print** Outs to standard output (usually terminal).

### First-class Citizens

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI4MjY5NjU1NiwxMDU5NDEzOTM2LDE3Mz
kxNzc0NzksMzA3MDE1NjY2LC0xNDU1NjE2NjgyLC0xNDgwNTg3
OTEsNDE1Njg4Mzk5XX0=
-->