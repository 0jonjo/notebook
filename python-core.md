# Python Core - Sololearn 

Dá para fazer operações matemáticas dentro de um print
O resultado de qualquer divisão (mesmo inteiros) é sempre float
Sempre que há um float envolvido em operação matemática, o resultado é em float
Raiz quadrada print( 9 ** (1/2) )
print('Brian\'s mother: He\'s not an angel. He\'s a very naughty boy!') - uso dos ' e " dentro do print
Backslashes can also be used to escape tabs, arbitrary Unicode characters, and various other things that can't be reliably printed.
Newlines will be automatically added for strings that are created using three quotes. 
Variáveis. The only characters that are allowed are letters, numbers, and underscores

# Walrus operator := 
allows you to assign values to variables within an expression, including variables that do not exist yet.
Ex: print(num:=int(input()))  
my_boolean = True print(my_boolean) #True print(2 == 3) #False
Greater than and smaller than operators can also be used to compare strings lexicographically (the alphabetical order of words is based on the alphabetical order of their component letters).
words = ["spam", "egg", "spam", "sausage"]
print("spam" in words) #True
nums = [1, 2, 3]
print(not 4 in nums) #True
print(4 not in nums) #True
Similar to while loops, the break and continue statements can be used in for loops, to stop the loop or jump to the next iteration.
The range() function returns a sequence of numbers.
By default, it starts from 0, increments by 1 and stops before the specified number.
Remember, the second argument is not included in the range, so range(3, 8) will not include the number 8. 
Range can have a third argument, which determines the interval of the sequence produced, also called the step. 
numbers = list(range(5, 20, 2))
for i in range(5):
    print("hello!")
 You don't need to call list on the range object when it is used in a for loop, because it isn't being indexed, so a list isn't required.
For a large programming project to be successful, it is essential to abide by the Don't Repeat Yourself, or DRY, principle
 Bad, repetitive code is said to abide by the WET principle, which stands for Write Everything Twice, or We Enjoy Typing.
Any statement that consists of a word followed by information in parentheses is a function call. 
 The words in front of the parentheses are function names, and the comma-separated values inside the parentheses are function arguments. 
Function arguments can be used as variables inside the function definition. However, they cannot be referenced outside of the function's definition. This also applies to other variables created inside a function.

# Docstrings (documentation strings)
 serve a similar purpose to comments, as they are designed to explain code. However, they are more specific and have a different syntax.
 def shout(word):
    """
    Print a word with an
    exclamation mark following it.
    """
    print(word + "!")

shout("spam")

Unlike conventional comments, docstrings are retained throughout the runtime of the program. This allows the programmer to inspect these comments at run time.
 functions are just like any other kind of value. They can be assigned and reassigned to variables, and later referenced by those names. 
Functions can also be used as arguments of other functions.
 * imports all objects from a module. For example: from math import *
This is generally discouraged, as it confuses variables in your code with variables in the external module.
There are three main types of modules in Python, those you write yourself, those you install from external sources, and those that are preinstalled with Python. 
The last type is called the standard library, and contains many useful modules. Some of the standard library's useful modules include string, re, datetime, math, random, os, multiprocessing, subprocess, socket, email, json, doctest, unittest, pdb, argparse and sys.

Tasks that can be done by the standard library include string parsing, data serialization, testing, debugging and manipulating dates, emails, command line arguments, and much more

# Exceptions
Different exceptions are raised for different reasons.
Common exceptions:
ImportError: an import fails;
IndexError: a list is indexed with an out-of-range number;
NameError: an unknown variable is used;
SyntaxError: the code can't be parsed properly;
TypeError: a function is called on a value of an inappropriate type;
ValueError: a function is called on a value of the correct type, but with an inappropriate value. 
- Exception Handling
A try statement can have multiple different except blocks to handle different exceptions.
Multiple exceptions can also be put into a single except block using parentheses, to have the except block handle all of them.
try:
    variable = 10
    print(variable + "hello")
    print(variable / 2)
except ZeroDivisionError:
    print("Divided by zero")
except (ValueError, TypeError):
    print("Error occurred")
An except statement without any exception specified will catch all errors. These should be used sparingly, as they can catch unexpected errors and hide programming mistakes.
- finally
To ensure some code runs no matter what errors occur, you can use a finally statement. The finally statement is placed at the bottom of a try/except statement. 
- Raising Exceptions
Exceptions can be raised with arguments that give detail about them.
For example:
name = "123"
raise NameError("Invalid name!")
In except blocks, the raise statement can be used without arguments to re-raise whatever exception occurred. 

# Assertions
An assertion is a sanity-check that you can turn on or turn off when you have finished testing the program.
Programmers often place assertions at the start of a function to check for valid input, and after a function call to check for valid output.
print(1)
assert 2 + 2 == 4
print(2)
assert 1 + 1 == 3
print(3) 

temp = -10
assert (temp >= 0), "Colder than absolute zero!"

# Reading Files
To retrieve each line in a file, you can use the readlines method to return a list in which each element is a line in the file. 
You can also use a for loop to iterate through the lines in the file
for line in file:	
	print(line)
file.close()

# Writing Files
To write to files you use the write method, which writes a string to the file.
The "w" mode will create a file, if it does not already exist.
When a file is opened in write mode, the file's existing content is deleted.
To write something other than a string, it needs to be converted to a string first.
- Working with Files
It is good practice to avoid wasting resources by making sure that files are always closed after they have been used. One way of doing this is to use try and finally
try:
   f = open("filename.txt")
   print(f.read())
finally:
   f.close()
An alternative way of doing this is using with statements. This creates a temporary variable (often called f), which is only accessible in the indented block of the with statement. 
with open("filename.txt") as f:
   print(f.read())
with open("filename.txt") as f:
   print(f.read())

The None object is used to represent the absence of a value.
It is similar to null in other programming languages.
Like other "empty" values, such as 0, [] and the empty string, it is False when converted to a Boolean variable.

# Dictionaries 
are data structures used to map arbitrary keys to values.
Lists can be thought of as dictionaries with integer keys within a certain range.
Dictionaries can be indexed in the same way as lists, using square brackets containing keys
ages = {"Dave": 24, "Mary": 42, "John": 58}
print(ages["Dave"])
print(ages["Mary"])
Each element in a dictionary is represented by a key:value pair. 
Only immutable objects can be used as keys to dictionaries.  So far, the only mutable objects you've come across are lists and dictionaries. Trying to use a mutable object as a dictionary key causes a TypeError.
Just like lists, dictionary keys can be assigned to different values.
However, unlike lists, a new dictionary key can also be assigned a value, not just ones that already exist. 
squares = {1: 1, 2: 4, 3: "error", 4: 16,}
squares[8] = 64
squares[3] = 9
print(squares)
To determine whether a key is in a dictionary, you can use in and not in, just as you can for a list.  
 nums = {
    1: "one",
    2: "two",
    3: "three",
}
print(1 in nums) #True
print("three" in nums) #False
print(4 not in nums) #True
- A useful dictionary method is get. It does the same thing as indexing, but if the key is not found in the dictionary it returns another specified value instead ('None', by default). 
print(pairs.get(12345, "not in dictionary"))

# Tuples 
are very similar to lists, except that they are immutable (they cannot be changed).
Also, they are created using parentheses, rather than square brackets. 
Tuples can be created without the parentheses, by just separating the values with commas. 
my_tuple = "one", "two", "three"
An empty tuple is created using an empty parenthesis pair.
tpl = ()
Tuples are faster than lists, but they cannot be changed.

# List slices 
provide a more advanced way of retrieving values from a list. Basic list slicing involves indexing a list with two colon-separated integers. This returns a new list containing all the values in the old list between the indices. 
squares = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
print(squares[2:6])
print(squares[3:8])
print(squares[0:1])
print(squares[:7])
print(squares[7:])
Like the arguments to range, the first index provided in a slice is included in the result, but the second isn't.
Slicing can also be done on tuples.

# List slices 
can also have a third number, representing the step, to include only alternate values in the slice. 
squares = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
print(squares[::2])
print(squares[2:8:3])
- When negative values are used for the first and second values in a slice (or a normal index), they count from the end of the list.
If a negative value is used for the step, the slice is done backwards.
Using [::-1] as a slice is a common and idiomatic way to reverse a list.

# List comprehensions 
are a useful way of quickly creating lists whose contents obey a simple rule. 
cubes = [i**3 for i in range(5)]
print(cubes)
- A list comprehension can also contain an if statement
evens=[i**2 for i in range(10) if i**2 % 2 == 0]
print(evens)
Trying to create a list in a very extensive range will result in a MemoryError. 
even = [2*i for i in range(10**100)]
-
# string formatting
String formatting provides a more powerful way to embed non-strings within strings. String formatting uses a string's format method to substitute a number of arguments in the string. 
nums = [4, 5, 6]
msg = "Numbers: {0} {1} {2}". format(nums[0], nums[1], nums[2])
print(msg)

print("{0}{1}{0}".format("abra", "cad"))

a = "{x}, {y}".format(x=5, y=12)
print(a)

# String Functions
Python contains many useful built-in functions and methods to accomplish common tasks.
join - joins a list of strings with another string as a separator.
replace - replaces one substring in a string with another.
startswith and endswith - determine if there is a substring at the start and end of a string, respectively.
To change the case of a string, you can use lower and upper.
The method split is the opposite of join turning a string with a certain separator into a list.
Some examples:

print(", ".join(["spam", "eggs", "ham"]))
#prints "spam, eggs, ham"
print("Hello ME".replace("ME", "world"))
#prints "Hello world"
print("This is a sentence.".startswith("This"))
# prints "True"
print("This is a sentence.".endswith("sentence."))
# prints "True"
print("This is a sentence.".upper())
# prints "THIS IS A SENTENCE."
print("AN ALL CAPS SENTENCE".lower())
#prints "an all caps sentence"
print("spam, eggs, ham".split(", "))
#prints "['spam', 'eggs', 'ham']"

#Numeric Functions
To find the maximum or minimum of some numbers or a list, you can use max or min.
To find the distance of a number from zero (its absolute value), use abs.
To round a number to a certain number of decimal places, use round.
To find the total of a list, use sum. 

print(min(1, 2, 3, 4, 0, 2, 1))
print(max([1, 4, 9, 2, 5, 6, 8]))
print(abs(-99))
print(abs(42))
print(sum([1, 2, 3, 4, 5]))

def count_char(text, char):
    count = 0
    for c in text:
        if c == char:
            count += 1
    return count

#Text Analyzer

file = open("newfile.txt", "w")
file.write("""Ornhgvshy vf orggre guna htyl.
Rkcyvpvg vf orggre guna vzcyvpvg.
Fvzcyr vf orggre guna pbzcyvpngrq.
Syng vf orggre guna arfgrq.
Fcenfr fv orggre guna qrafr.
Ernqnovyvgl pbhagf.
Fcrpvny pnfrf nera'g fcrpvny rabthu gb oernx gur ehyrf.
Nygubhtu cenpgvpnyvgl orgnf chevgl.
Reebef fubhyq arire cnff fvyragyl.
Hayrff rkcyvpvgyl fvyraprq.
Va gur snpr bs nzovthvgl, ershfr gur grzcgngvba bg thrff.
Gurer fubhyq or bar-- naq cersrenoylbayl bar --boivbhf jnl gb qb vg.
Nygubhtu gung jnl znl abg or boivbhf ng svefg hayrff lbh'er Qhgpu.
Abj vf orggre guna arrire.
Nygubhtu arire vf bsgra orggre guna *evtug* abj.
Vs gur vzcyrzragngvba vf uneq gb rkcynva, vg'f n onq vqrn.
Vs gur vzcyrzragngvba vf rnfl gb rkcynva, vg znl or n tbbq vqrn.
Anzrfcnprf ner bar ubaxvat terng vqrn -- yrg'f qb zber bs gubfr!""")
file.close()

filename = "newfile.txt"
with open(filename) as f:
    text = f.read()

for char in "abcdefghijklmnopqrstuvwxyz":
    perc = 100 * count_char(text, char) / len(text)
    print("{0} - {1}%".format(char, round(perc, 2)))
    
# Longest Word

Given a text as input, find and output the longest word.

Sample Input
this is an awesome text

Sample Output
awesome 

txt = input()

words = txt.split(' ')

print (max(words, key=len))

# Functional Programming
Functional programming is a style of programming that (as the name suggests) is based around functions.
A key part of functional programming is higher-order functions. We have seen this idea briefly in the previous lesson on functions as objects. Higher-order functions take other functions as arguments, or return them as results. 

def apply_twice(func, arg):
    return func(func(arg))

def add_five(x):
    return x + 5

print(apply_twice(add_five, 10))

# Pure Functions
Functional programming seeks to use pure functions. Pure functions have no side effects, and return a value that depends only on their arguments. This is how functions in math work: for example, The cos(x) will, for the same value of x, always return the same result.

Impure function:
some_list = []

> def impure(arg):
>  some_list.append(arg)
> The function above is not pure, because it changed the state of some_list.

Using pure functions has both advantages and disadvantages.
Pure functions are:
- easier to reason about and test.
- more efficient. Once the function has been evaluated for an input, the result can be stored and referred to the next time the function of that input is needed, reducing the number of times the function is called. This is called memoization.
- easier to run in parallel. 

The main disadvantage of using only pure functions is that they majorly complicate the otherwise simple task of I/O, since this appears to inherently require side effects. They can also be more difficult to write in some situations.

# Lambda

The same is possible with functions, provided that they are created using lambda syntax. Functions created this way are known as anonymous. This approach is most commonly used when passing a simple function as an argument to another function. The syntax is shown in the next example and consists of the lambda keyword followed by a list of arguments, a colon, and the expression to evaluate and return. 
Lambda functions aren't as powerful as named functions.
They can only do things that require a single expression - usually equivalent to a single line of code.
Example: 

#named function
def polynomial(x):
    return x**2 + 5*x + 4
print(polynomial(-4))

#lambda
print((lambda x: x**2 + 5*x + 4) (-4))

# Map
The built-in functions map and filter are very useful higher-order functions that operate on lists (or similar objects called iterables).
The function map takes a function and an iterable as arguments, and returns a new iterable with the function applied to each argument.

def add_five(x):
    return x + 5

nums = [11, 22, 33, 44, 55]
result = list(map(add_five, nums))
print(result)

# filter
The function filter filters an iterable by removing items that don't match a predicate (a function that returns a Boolean). 

nums = [11, 22, 33, 44, 55]
res = list(filter(lambda x: x%2==0, nums))
print(res)

Like map, the result has to be explicitly converted to a list if you want to print it.

# Generators
Generators are a type of iterable, like lists or tuples. Unlike lists, they don't allow indexing with arbitrary indices, but they can still be iterated through with for loops. They can be created using functions and the yield statement. 

def countdown():
    i=5
    while i > 0:
        yield i
        i -= 1

for i in countdown():
    print(i)

Finite generators can be converted into lists by passing them as arguments to the list function.

def numbers(x):
    for i in range(x):
        if i % 2 == 0:
            yield i

print(list(numbers(11)))

Using generators results in improved performance, which is the result of the lazy (on demand) generation of values, which translates to lower memory usage. Furthermore, we do not need to wait until all the elements have been generated before we start to use them.  #Decorators Decorators provide a way to modify functions using other functions.  This is ideal when you need to extend the functionality of functions that you don't want to modify.  def decor(func): def wrap(): print("============") func()
        print("============")
    return wrap

def print_text():
    print("Hello world!")

print_text = decor(print_text)

print_text();

Python provides support to wrap a function in a decorator by pre-pending the function definition with a decorator name and the @ symbol.
If we are defining a function we can "decorate" it with the @ symbol like:

def decor(func):
    def wrap():
        print("============")
        func()
        print("============")
    return wrap

def print_text():
    print("Hello world!")

print_text = decor(print_text)

print_text();

A single function can have multiple decorators.

#Recursion
Recursion is a very important concept in functional programming.
The fundamental part of recursion is self-reference - functions calling themselves. It is used to solve problems that can be broken up into easier sub-problems of the same type.

def factorial(x):
    if x == 1:
        return 1
    else: 
        return x * factorial(x-1)

print(factorial(5))

Furthermore, 1! = 1. This is known as the base case, as it can be calculated without performing any more factorials. 
The base case acts as the exit condition of the recursion.

Recursive functions can be infinite, just like infinite while loops. These often occur when you forget to implement the base case. 

Recursion can also be indirect. One function can call a second, which calls the first, which calls the second, and so on. This can occur with any number of functions. Example:

def is_even(x):
    if x == 0:
        return True
    else:
        return is_odd(x-1)

def is_odd(x):
    return not is_even(x)

print(is_odd(17))
print(is_even(23))

# Sets
Sets are data structures, similar to lists or dictionaries. They are created using curly braces, or the set function. They share some functionality with lists, such as the use of in to check whether they contain a particular item.

num_set = {1, 2, 3, 4, 5}
word_set = set(["spam", "eggs", "sausage"])

print(3 in num_set)
print("spam" not in word_set)

Sets differ from lists in several ways, but share several list operations such as len.
They are unordered, which means that they can't be indexed.
They cannot contain duplicate elements.
Due to the way they're stored, it's faster to check whether an item is part of a set, rather than part of a list.
Instead of using append to add to a set, use add.
The method remove removes a specific element from a set; pop removes an arbitrary element. Basic uses of sets include membership testing and the elimination of duplicate entries.

nums = {1, 2, 1, 3, 1, 4, 5, 6}
print(nums)
nums.add(-7)
nums.remove(3)
print(nums)

Sets can be combined using mathematical operations.
The union operator | combines two sets to form a new one containing items in either.
The intersection operator & gets items only in both.
The difference operator - gets items in the first set but not in the second.
The symmetric difference operator ^ gets items in either set, but not both.

first = {1, 2, 3, 4, 5, 6}
second = {4, 5, 6, 7, 8, 9}

print(first | second)
print(first & second)
print(first - second)
print(second - first)
print(first ^ second)

# Data Structures
As we have seen in the previous lessons, Python supports the following data structures: lists, dictionaries, tuples, sets.

When to use a dictionary:
- When you need a logical association between a key:value pair.
- When you need fast lookup for your data, based on a custom key.
- When your data is being constantly modified. Remember, dictionaries are mutable.

When to use the other types:
- Use lists if you have a collection of data that does not need random access. Try to choose lists when you need a simple, iterable collection that is modified frequently.
- Use a set if you need uniqueness for the elements.
- Use tuples when your data cannot change. 

Many times, a tuple is used in combination with a dictionary, for example, a tuple might represent a key, because it's immutable. 

# itertools

The module itertools is a standard library that contains several functions that are useful in functional programming.
One type of function it produces is infinite iterators.
The function count counts up infinitely from a value.
The function cycle infinitely iterates through an iterable (for instance a list or string).
The function repeat repeats an object, either infinitely or a specific number of times. 

from itertools import count

for i in count(3):
    print(i)
    if i >=11:
        break
        
Obs: cuidado para o laço não fica infinito.

There are many functions in itertools that operate on iterables, in a similar way to map and filter.
Some examples:
takewhile - takes items from an iterable while a predicate function remains true;
chain - combines several iterables into one long one;
accumulate - returns a running total of values in an iterable.

There are also several combinatoric functions in itertool, such as product and permutation.
These are used when you want to accomplish a task with all possible combinations of some items. 
from itertools import product, permutations

letters = ("A", "B")
print(list(product(letters, range(2))))
print(list(permutations(letters))) 

# Fibonnaci Problem

num = int(input())


def fibonacci(n):

	ultimo = 1
	penultimo = 0

	for count in range(n):
		if count <= 1:
			print(count)
		else:
			termo = ultimo + penultimo
			penultimo = ultimo
			ultimo = termo
			count += 1
			print(termo)

fibonacci(num)

# Classes

We have previously looked at two paradigms of programming - imperative (using statements, loops, and functions as subroutines), and functional (using pure functions, higher-order functions, and recursion).
Classes are created using the keyword class and an indented block, which contains class methods (which are functions). 

class Cat:
  def __init__(self, color, legs):
    self.color = color
    self.legs = legs

felix = Cat("ginger", 4)
print(felix.color)

# __init__

The __init__ method is the most important method in a class. The __init__ method is called the class constructor. 
This is called when an instance (object) of the class is created, using the class name as a function.
All methods must have self as their first parameter, although it isn't explicitly passed, Python adds the self argument to the list for you; you do not need to include it when you call the methods. Within a method definition, self refers to the instance calling the method.
Instances of a class have attributes, which are pieces of data associated with them.
In this example, Cat instances have attributes color and legs. These can be accessed by putting a dot, and the attribute name after an instance. In an __init__ method, self.attribute can therefore be used to set the initial value of an instance's attributes.

# Methods
Classes can have other methods defined to add functionality to them.
Remember, that all methods must have self as their first parameter.
Classes can also have class attributes, created by assigning variables within the body of the class. These can be accessed either from instances of the class, or the class itself.

# Inheritance
To inherit a class from another class, put the superclass name in parentheses after the class name.

class Animal:
	def __init__(self, name, color):
	self.name = name
	self.color = color

class Cat(Animal):
	def purr(self):
		print("Purr...")

Inheritance can also be indirect. One class can inherit from another, and that class can inherit from a third class.

# Super
The function super is a useful inheritance-related function that refers to the parent class. It can be used to find the method with a certain name in an object's superclass. 

class A:
	def spam(self):
		print(1)
class B(A):
	def spam(self)
		print(2)
		super().spam()
B().spam()
- 2
- 1 (calls the spam method of the superclass.)

# Magic Methods
Magic methods are special methods which have double underscores at the beginning and end of their names.
They are also known as **dunders**.
So far, the only one we have encountered is __init__, but there are several others.
They are used to create functionality that can't be represented as a normal method.

One common use of them is operator overloading.
This means defining operators for custom classes that allow operators such as + and * to be used on them.
An example magic method is __add__ for +. It adds the corresponding attributes of the objects and returns a new object, containing the result.
Once it's defined, we can add two objects of the class together.

class Vector2D:
	def __init__(self, x, y):
		self.x = x
		self.y = y
	def __add__(self, other)
		return Vector2D(self.x + other.x, self.y + other.y)
first = Vector2D(5, 7)
second = Vector2D(3, 9)
result = first + second
print(result.x) // 8 
print (result.y) // 16  

More magic methods for common operators:
__sub__ for -
__mul__ for *
__truediv__ for /
__floordiv__ for //
__mod__ for %
__pow__ for **
__and__ for &
__xor__ for ^
__or__ for |

The expression x + y is translated into x.__add__(y).
However, if x hasn't implemented __add__, and x and y are of different types, then y.__radd__(x) is called.

Python also provides magic methods for comparisons.
__lt__ for <
__le__ for <=
__eq__ for ==
__ne__ for !=
__gt__ for >
__ge__ for >=

If __ne__ is not implemented, it returns the opposite of __eq__
As you can see, you can define any custom behavior for the overloaded operators.

There are several magic methods for making classes act like containers.
__len__ for len()
__getitem__ for indexing
__setitem__ for assigning to indexed values
__delitem__ for deleting indexed values
__iter__ for iteration over objects (e.g., in for loops)
__contains__ for in

There are many other magic methods that we won't cover here, such as __call__ for calling objects as functions, and __int__, __str__, and the like, for converting objects to built-in types.

# Object Lifecycle
When an object is destroyed, the memory allocated to it is freed up, and can be used for other purposes.
Destruction of an object occurs when its reference count reaches zero. Reference count is the number of variables and other elements that refer to an object.
If nothing is referring to it (it has a reference count of zero) nothing can interact with it, so it can be safely deleted.

In some situations, two (or more) objects can be referred to by each other only, and therefore can be deleted as well.

The del statement reduces the reference count of an object by one, and this often leads to its deletion.
The magic method for the del statement is __del__.
The process of deleting objects when they are no longer needed is called garbage collection.
In summary, an object's reference count increases when it is assigned a new name or placed in a container (list, tuple, or dictionary). The object's reference count decreases wheN it's deleted with del, its reference is reassigned, or its reference goes out of scope. When an object's reference count reaches zero, Python automatically deletes it.

a = 42  # Create object <42>
b = a  # Increase ref. count  of <42> 
c = [a]  # Increase ref. count  of <42> 

del a  # Decrease ref. count  of <42>
b = 100  # Decrease ref. count  of <42> 
c[0] = -1  # Decrease ref. count  of <42>

Lower level languages like C don't have this kind of automatic memory management.

# Data Hiding
A key part of object-oriented programming is encapsulation, which involves packaging of related variables and functions into a single easy-to-use object - an instance of a class.
The Python philosophy is slightly different. It is often stated as "we are all consenting adults here", meaning that you shouldn't put arbitrary restrictions on accessing parts of a class. Hence there are no ways of enforcing a method or attribute be strictly private. 
However, there are ways to discourage people from accessing parts of a class, such as by denoting that it is an implementation detail, and should be used at their own risk.

Weakly private methods and attributes have a single underscore at the beginning.
This signals that they are private, and shouldn't be used by external code. However, it is mostly only a convention, and does not stop external code from accessing them.
Its only actual effect is that from module_name import * won't import variables that start with a single underscore.

class Quene
	def __init__(self, contents):
	self._hiddenList = list(contents)

Strongly private methods and attributes have a double underscore at the beginning of their names. This causes their names to be mangled, which means that they can't be accessed from outside the class.
The purpose of this isn't to ensure that they are kept private, but to avoid bugs if there are subclasses that have methods or attributes with the same names.
Name mangled methods can still be accessed externally, but by a different name. The method __privatemethod of class Spam could be accessed externally with* _Spam__privatemethod*.
Example:

class Spam:
	__egg = 7
	def print_egg(self):
		print(self.__egg)
s = Spam()
s.print__egg()
print(s._Spam__egg)
print(s.__egg) 

Basically, Python protects those members by internally changing the name to include the class name.

# Class Methods
Methods of objects we've looked at so far are called by an instance of a class, which is then passed to the self parameter of the method.
Class methods are different - they are called by a class, which is passed to the cls parameter of the method.
A common use of these are factory methods, which instantiate an instance of a class, using different parameters than those usually passed to the class constructor.
Class methods are marked with a classmethod decorator.
Example:

class Rectangle:
	def __init__ (self, width, height):
		self.width = width
		self.height = height

	def calculate_area(self):
		return self.width * self.height

	@classmethod
	def new_square(cls, side_lenght):
		return cls(side_lenght, side_lenght)

square = Rectangle.new_square(5)
print(square.calculate_area())

new_square is a class method and is called on the class, rather than on an instance of the class. It returns a new object of the class cls.

Technically, the parameters self and cls are just conventions; they could be changed to anything else. However, they are universally followed, so it is wise to stick to using them.

# Static Methods
Static methods are similar to class methods, except they don't receive any additional arguments; they are identical to normal functions that belong to a class.
They are marked with the staticmethod decorator.

@staticmethod
def validate(topping):

Static methods behave like plain functions, except for the fact that you can call them from an instance of the class.

# Properties

Properties provide a way of customizing access to instance attributes.
They are created by putting the property decorator above a method, which means when the instance attribute with the same name as the method is accessed, the method will be called instead.
One common use of a property is to make an attribute read-only.

@property
def pinaple_allowed(self):
	return False


Properties can also be set by defining setter/getter functions.
The setter function sets the corresponding property's value.
The getter gets the value.
To define a setter, you need to use a decorator of the same name as the property, followed by a dot and the setter keyword.
The same applies to defining getter functions. 

@property.allowed.setter
def pinaple_allowed(self, value):
	if value:
		password = "teste"
		self._pinapple_allowed = value
	else:
		raise ValueError("Alert! Intruder!")

# Lista de exercícios Classe em Python
https://auladecomputacao.files.wordpress.com/2020/07/lista-de-exercicios-poo_python-e-java.pdf

- Tomar cuidado para usar o self. nas funções corretamente
 
# Regular Expressions

Regular expressions are a powerful tool for various kinds of string manipulation
They are a domain specific language (DSL) that is present as a library in most modern programming languages, not just Python.
They are useful for two main tasks:
- verifying that strings match a pattern (for instance, that a string has the format of an email address),
- performing substitutions in a string (such as changing all American spellings to British ones).

Regular expressions in Python can be accessed using the re module, which is part of the standard library.
After you've defined a regular expression, the re.match function can be used to determine whether it matches at the beginning of a string.
If it does, match returns an object representing the match, if not, it returns None.
To avoid any confusion while working with regular expressions, we would use raw strings as r"expression".
Raw strings don't escape anything, which makes use of regular expressions easier.

Other functions to match patterns are re.search and re.findall.
The function re.search finds a match of a pattern anywhere in the string.
The function re.findall returns a list of all substrings that match a pattern.

The regex search returns an object with several methods that give details about it.
These methods include group which returns the string matched, start and end which return the start and ending positions of the first match, and span which returns the start and end positions of the first match as a tuple.   

# Groups

The content of groups in a match can be accessed using the group function.
A call of group(0) or group() returns the whole match.
A call of group(n), where n is greater than 0, returns the nth group from the left.
The method groups() returns all groups up from 1. 


There are several kinds of special groups.
Two useful ones are named groups and non-capturing groups.
Named groups have the format (?P<name>...), where name is the name of the group, and ... is the content. They behave exactly the same as normal groups, except they can be accessed by group(name) in addition to its number.
Non-capturing groups have the format (?:...). They are not accessible by the group method, so they can be added to an existing regular expression without breaking the numbering. 

Metacharacters

Another important metacharacter is |.
This means "or", so red|blue matches either "red" or "blue". 

pattern = r"gr(a|e)y"

# Special Sequences

There are various special sequences you can use in regular expressions. They are written as a backslash followed by another character.
One useful special sequence is a backslash and a number between 1 and 99, e.g., \1 or \17. This matches the expression of the group of that number.

import re

pattern = r"(.+) \1"

match = re.match(pattern, "word word")
if match:
	print ("Match 1")

More useful special sequences are \d, \s, and \w.
These match digits, whitespace, and word characters respectively.
In ASCII mode they are equivalent to [0-9], [ \t\n\r\f\v], and [a-zA-Z0-9_].
In Unicode mode they match certain other characters, as well. For instance, \w matches letters with accents.
Versions of these special sequences with upper case letters - \D, \S, and \W - mean the opposite to the lower-case versions. For instance, \D matches anything that isn't a digit.


Additional special sequences are \A, \Z, and \b.
The sequences \A and \Z match the beginning and end of a string, respectively.
The sequence \b matches the empty string between \w and \W characters, or \w characters and the beginning or end of the string. Informally, it represents the boundary between words.
The sequence \B matches the empty string anywhere else. 

Email Extraction


To demonstrate a sample usage of regular expressions, lets create a program to extract email addresses from a string. Suppose we have a text that contains an email address: 

import re

pattern = r"([\w\.-]+)@([\w\.-]+)(\.[\w\.]+)"
str = "Please contact info@sololearn.com for assistance"

match = re.search(patern, str)
if match
	print(match.group())

[\w\.-]+ matches one or more word character, dot or dash.
The regex above says that the string should contain a word (with dots and dashes allowed), followed by the @ sign, then another similar word, then a dot and another word.
Our regex contains three groups:
1 - first part of the email address.
2 - domain name without the suffix.
3 - the domain suffix.  
