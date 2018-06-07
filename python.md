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
If a variable should not have an initial value, then one can assign it `None`.
### Functions
The basic syntax of a Python function follows standard function declaration formats i.e.
```python
def <function name>(<parameters, if any>):
````
followed by code. All code must be indented by one and only one indent following a function declaration. There is no return type.
### Conditions
There is a single conditional in Python, which is the {\em if...elif...else}. Unlike other languages, there is no switch. The syntax
```python
if (not) <condition> (and|or) <condition> .... :
```
Python does not use operators such as `!`, `&`, and `||` to denote negation, and, or but instead uses `not`, `and`,  `or`, respectively. Using the symbols results in a `SyntaxError`. There is also another operator which is `in`, allowing one to test for membership within a collection. For example,
```python
'hello' in 'hello world'

OR

1 in [1, 2, 3, 4]

OR

'apples' not in ['pears', 'lemons', 'grapes']
```
#### Ternary Operators
Python does not have a ternary operator (`<condition> ? <execute if true> : <execute if false>`) and this was a design choice.
Instead, one can use a modified if else:
```python
<value if condition true> if <condition> else <value if condition false

E.G.

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

E.G.

lst = [1, 23, 44, 3]
for i in lst:
	print(i)

OUTPUT IS
1
23
44
3
 ```
The above assigns `<variable>` a value of an element in the list or tuple. If one also needs the index, then one would do
```python
for <index-variable>, <value-variable> in enumerate(<some-list-set-or-tuple>):
	<code>

E.G.

lst = [1, 23, 44, 3]
for i, v in enumerate(lst):
	print(i,v)

OUTPUT IS
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
#WITHOUT USING for...else
found = 0
for name in names:
	if name == 'John':
    	<code>
        found = 1
        break
if found == 0:
	<name not found code>
<other code>

#WITH USING for...else

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
    
#IF INHERITING:

class <class name>(<classes inherited from>):
	<functions>
```
The constructor for a class is a special function called the \_\_init\_\_ function, which is empty by default.

All instance functions are defined as follows:
```python
def <function name>(<self-reference-variable>, <variables>):
	<code>
```
The first variable of an instance function is the *self variable*, which is traditionally called "self" but can be called anything one wants, is used to reference instance functions and variables (e.g. `self.variable` or `self.function()`). If one is making a static function (or static method, as it is so called in Python), then the first parameter is not the *self parameter* and alos must append the @classmethod decorator to the line abov, e.g.
\begin{Verbatim}[xleftmargin=.5in]
@classmethod
def <function-name>(<variables):
	<code
\end{Verbatim}
Creating an instance of a class is just like any other OOP language:
\begin{Verbatim}[xleftmargin=.5in]
class A:
	def __init__(self, value):
    	self.value = value
    def increment(self):
    	self.value += 1
    def get_increment(self):
    	self.increment()
        return self.value
        
a = A(10)
\end{Verbatim}
\subsubsection{Notes}
Java does not allow inheriting from multiple classes as that runs into the diamond problem, which is if a class C inherits from
classes A and B and they each have a foo() function inside with the same method signature, which one do you run? Python solves
this by using the order of inheritence so if one did class C(A,B) it would check A for foo() then B for foo().

\section{Programming Constructs}
\subsection{Lambdas}
Sometimes there is something that can be done by a function but it is a single line, or one is in a situation where there is
a function that requires another function as an argument but it is only a single-line function. At this point, one would use
a lambda, which can be thought of as an anonymous function:
\begin{verbatim}
lambda <variables>: <expression>
\end{verbatim}
The value of <expression> is returned from the function (if it does not return anything, for example if it is a print statement,
it returns None). Lambdas can also be assigned to variables as well.
\subsection{Comprehensions}
One of Python's most powerful tools is its ability to perform comprehensions. These are very useful when one wishes to produce
a list from a dataset. For example, let us make a list of the squares of numbers from 0 to 9.
\begin{Verbatim}[xleftmargin=.5in]
IN C99:

int squares[10];
int i;
for (i = 0; i < 10; i++) {
	squares[i] = i * i;
}

IN JAVA

int[] squares = new int[10];
for (int i = 0; i < 10; i++) {
	squares[i] = i * i;
}

IN PYTHON WITH LIST COMPREHENSIONS

squares = [i * i for i in range(10)]
\end{Verbatim}
While a trivial example, list comprehensions allows programmers to shrink code that would take multiple lines into a single expression. The most basic form of the list comprehension is:
\begin{verbatim}
[<expression with variable> for <variable> in <collection>]

e.g.

[foo(i) for i in [1, 2, 3, 4, 5]]

OR

[(k,v) for k,v in dictionary.items()]
\end{verbatim}
One can also do some basic filtering in these comprehensions
\begin{verbatim}
a = [<expression w/ variable> for <variable> in <collection> if <condition>]

E.G.

a = [i * i for i in range(10) if i % 2 == 0]
	^-- generate list of squares for positive numbers only
\end{verbatim}
One can also nest list comprehensions
\begin{verbatim}
sent = "This is a sentence with words"
sent_long_words_only = [word for word in [word.lower() \
	for word in sent.split(' ')] if len(word) > 4]
\end{verbatim}
However, this is not only for lists. This can be used for dicts as well:
\begin{verbatim}
{<key>: <value> for <variables> in <collection>}
E.G.

some_dict = {k: foo(k) for k in a_list}
\end{verbatim}

\subsection{Useful built-in functions}
Python provided a lot of useful built-in functions as well.

{\bf map} The {\em map} function is very useful in taking a collection and apply a given function to it. This is very similar
to a list comprehension however map is lazy unlike comprehensions which are eager. Sometimes, we might not need an entire list
at once but small chunks or even a single element of it, do some work on it, and go on to the next small segment. With a list
comprehension, all the data is always stored in memory which, if we are dealing with a lot of data, may not be the best thing
for us to do. With a map, only when we need that particular segment of the list is the data actually processed. For example,
if we have a list of names and want to pull the accounts associated with the names and send some notices, if there is a lot
of data per individual then it would be very expensive memory-wise to store all of that in a list. Instead, with a map, we can
pull data for a single name, process it, and then go on to the next one, which allows us to save space as we are storing a single
user's data at a time. This also comes with the drawback that we cannot reference a previous value in the map as it can be thought
of as removed from memory. However, if one uses a map and then wants to convert it to a list, then one can just apply the list()
function to the map and it will generate the list.
\begin{Verbatim}[xleftmargin=.5in]
SYNTAX

map(<function name or lambda>, collection)

E.G.

def send_notices(username):
	data = get_large_data(username)
    return send_notices_if_condition(data)
    
names = ['John Doe', 'Jane Hathaway', ... ]
notices_sent = map(send_notices, names)

OR

squares = map(lambda i: i * i, range(10))
\end{Verbatim}
{\bf filter} The {\em filter} function does what it sounds like it does: filters through a collection based on a specific criteria.
The function given must return a boolean.
\begin{verbatim}
filter(<test function>, <collection>)

e.g.

evens = filter(lambda i: i % 2 == 0, range(100))
\end{verbatim}
filter is lazy as well.
{\bf sorted} The {\em sorted} function sorts a list. However, it is destructive, as in it modifies the original list. Given a simple
list like an array of integers it will sort it how one expects it to (unlike Javascript). However, if it is a list of tuples and one
wishes to sort by the second element, then one needs to give a key function, which specifies which element to sort by
\begin{verbatim}
a = [1, 11, 3, 4]
sorted(a)
a is now [1, 3, 4, 11]

WITH KEY FUNCTION

sorted(<collection>, <key function>)
a = [(3,2), (1,1), (4, -1)]
sorted(a) <--- [(1,1), (3,2), (4,-1)]
sorted(a, lambda k: k[1]) <--- [(4,-1), (1,1), (3,2)]

REVERSING
a = [4, 2, 3, 1]
sorted(a, reversed=True) <--- [4, 3, 2, 1]
\end{verbatim}
{\bf reversed} - Reverse an existing ordered collection (like a list). However, it is also lazy.

{\bf zip}

{\bf len}

{\bf dict, list, tuple, set}

{\bf open}

{\bf dir}

{\bf super}
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI4MzAxMzQxNSwtMTQ4MDU4NzkxLDQxNT
Y4ODM5OV19
-->