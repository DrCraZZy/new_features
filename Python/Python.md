# <u>Python</u>

## <u>Python Syntax</u>

### <u>Virtual environment erstellen</u>
```bash
python -m venv env
```
Enterpräter ändern zu dem in env
___.ipynb___ - Dateiendung für Jupyter

### <u>Install Jupyter Notebook in VS Code</u>

- Download Python extention
- Open new file (CTRL + N)
- F1 type "_Jupyter: create new jupyter notebook_"

### <U>Variablen</u>

```python
example_number = 1
example_float = 1.0
example_string = "Example String"
example_boolean = True
```

### <u>requirements.txt</u>
```bash
pip3 freeze > requirements.txt
```

### <U>Conditionals</u>
```python
if mood == "good":
  print("I am happy!")
else:
  print("I am grumpy!")

#oder 

if mood == "good":
  print("I am happy!")
elif mood == "bad":
  print("I am grumpy!")
else:
  print("I am smack-dab in the middle!")
```

### <U>Loops</u>
```python
# for - loop
answer = 0
for i in range(1, 10**9 + 1):
  answer += i

# while - loop
answer = 0
number = 0
while number < 10**9 + 1:
 answer += number
 number += 1
```

### <U>Data Structures</u>

### List
```python
# create list of strings
groceries = ['apples', 'oranges', 'avocados', 'grapes']

# empty list
my_list = list()
my_list = []

# list with mixed data types
my_list = [1, "Hello", 3.4]

# nested list
my_list = ["mouse", [8, 4, 6], ['a']]

# convert to list
lett_set = {'a', 'e', 'i', 'o', 'u'}
lett_list = list(lett_set)
```

```python
# Access list elements
my_list = ['p', 'r', 'o', 'b', 'e']

# List Index 
# first item
print(my_list[0])

# third item
print(my_list[2])

# Nested indexing
print(n_list[0][1])

# last item
print(my_list[-1])

# fifth last item
print(my_list[-5])

# ----------------------------------------------

# List slicing
# List slicing in Python

my_list = ['p','r','o','g','r','a','m','i','z']

# elements from index 2 to index 4
print(my_list[2:5])

# elements from index 5 to end
print(my_list[5:])

# elements beginning to end
print(my_list[:])
```

```python
# Add/Change List Elements
# Correcting mistake values in a list
odd = [2, 4, 6, 8]

# change the 1st item    
odd[0] = 1  # -> [1, 4, 6, 8]           

# change 2nd to 4th items
odd[1:4] = [3, 5, 7] # -> [1, 3, 5, 7]

# ----------------------------------------------

# Appending and Extending lists in Python
odd = [1, 3, 5]

odd.append(7) # -> [1, 3, 5, 7]

odd.extend([9, 11, 13]) # -> [1, 3, 5, 7, 9, 11, 13]

# ----------------------------------------------

# Concatenating and repeating lists
odd = [1, 3, 5]

odd + [9, 7, 5] # -> [1, 3, 5, 9, 7, 5]

["re"] * 3 # -> ['re', 're', 're']

# Demonstration of list insert() method
odd = [1, 9]

odd.insert(1,3) # -> [1, 3, 9]

odd[2:2] = [5, 7] # -> [1, 3, 5, 7, 9]
```

```python
# Deleting list items
my_list = ['p', 'r', 'o', 'b', 'l', 'e', 'm', 'z', 'x']

# delete one item
del my_list[2] # -> ['p', 'r', 'b', 'l', 'e', 'm', 'z', 'x']

# delete multiple items
del my_list[1:5] # -> ['p', 'm', 'z', 'x']

# delete the entire list
del my_list # -> NameError: name 'my_list' is not defined

# remove
my_list.remove('p') # -> ['m']

# pop - pop ohne Argumente pop() -> letzter element
my_list.pop(0) # -> m
my_list # -> ['z', 'x']

# clear
my_list.clear() # -> []
```

|Methods|Descriptions|
|---|---|
|append()|	adds an element to the end of the list|
|extend()|	adds all elements of a list to another list|
|insert()|	inserts an item at the defined index|
|remove()|	removes an item from the list|
|pop()|	returns and removes an element at the given index|
|clear()|	removes all items from the list|
|index()|	returns the index of the first matched item|
|count()|	returns the count of the number of items passed as an argument|
|sort()|	sort items in a list in ascending order|
|reverse()|	reverse the order of items in the list|
|copy() |	returns a shallow copy of the list|

### Tuple
Tuple ist wie eine Liste aber unveränderlich (immutable)

```python
# Empty tuple
my_tuple = ()

# Tuple having integers
my_tuple = (1, 2, 3)

# tuple with mixed datatypes
my_tuple = (1, "Hello", 3.4)

# nested tuple
my_tuple = ("mouse", [8, 4, 6], (1, 2, 3))

# tuple unpacking is also possible
my_tuple = 3, 4.6, "dog" # create tuple without parentheses 
a, b, c = my_tuple

# Creating a tuple having one element
my_tuple = ("hello",)

# Element access and slicing work like with a list
# Changing fo tuples is imposible because they are immutable
# but if the element in tuple is mutable, then is it posible
# to change an item

# Concatenation
print((1, 2, 3) + (4, 5, 6)) # -> (1, 2, 3, 4, 5, 6)

# Repeat
print(("Repeat",) * 3) # -> ('Repeat', 'Repeat', 'Repeat')

# can't delete items
del my_tuple[3] # -> TypeError: 'tuple' object doesn't support item deletion

# Can delete an entire tuple
del my_tuple

# tuple methods
my_tuple = ('a', 'p', 'p', 'l', 'e',)

print(my_tuple.count('p'))  # -> 2
print(my_tuple.index('l'))  # -> 3

# Membership test in tuple
my_tuple = ('a', 'p', 'p', 'l', 'e',)

# In operation
'a' in my_tuple # -> True
'b' in my_tuple # -> False

# Not in operation
'g' not in my_tuple # -> True

# Using a for loop to iterate through a tuple
for name in ('John', 'Kate'):
    print("Hello", name)
```

### Set
Sets sind für das Speichern der einzigartige Daten zu speichern (Daten ohne Wiederholungen).

```python
# Create Sets
# set of integers
my_set = {1, 2, 3} # -> {1, 2, 3}

# set of mixed datatypes
my_set = {1.0, "Hello", (1, 2, 3)} # -> {1.0, (1, 2, 3), 'Hello'}

# we can make set from a list
my_set = set([1, 2, 3, 2]) # -> {1, 2, 3}

# initialize a with {}
a = {} # -> <class 'dict'>

# initialize a with set()
a = set() # -> <class 'set'>

# Modifying a set
# initialize my_set
my_set = {1, 3}

# add an element
my_set.add(2) # -> {1, 2, 3}

my_set[0] # -> TypeError: 'set' object does not support indexing

# add multiple elements
my_set.update([2, 3, 4]) # -> {1, 2, 3, 4}

# add list and set
my_set.update([4, 5], {1, 6, 8}) # -> {1, 2, 3, 4, 5, 6, 8}

# Removing elements from a set, discard() and remove()
# initialize my_set
my_set = {1, 3, 4, 5, 6}
my_set.discard(4) # -> {1, 3, 5, 6}
my_set.remove(6) # -> {1, 3, 5}

# discard an element not present in my_set
my_set.discard(2) # -> {1, 3, 5}

# remove an element not present in my_set
my_set.remove(2) # -> KeyError

# pop an element
my_set.pop() # -> random element

# clear my_set
my_set.clear() # -> set()

# Set Operations
# Set Union

# Set union method initialize A and B
A = {1, 2, 3, 4, 5}
B = {4, 5, 6, 7, 8}

# use | operator
A | B # -> {1, 2, 3, 4, 5, 6, 7, 8}

# use union function
A.union(B) # -> {1, 2, 3, 4, 5, 6, 7, 8}
B.union(A) # -> {1, 2, 3, 4, 5, 6, 7, 8}

#Set Intersection
A & B # -> {4, 5}

#Set Difference
A - B # -> {1, 2, 3}
A.difference(B) # -> {1, 2, 3}


B - A # -> {8, 6, 7}
B.difference(A) # -> {8, 6, 7}


# Set Symmetric Difference
# use ^ operator
A ^ B # -> {1, 2, 3, 6, 7, 8}

A.symmetric_difference(B) # -> {1, 2, 3, 6, 7, 8}
B.symmetric_difference(A) # -> {1, 2, 3, 6, 7, 8}

# check if 'a' is present
'a' in my_set # -> True
'p' not in my_set # -> False

# Iteration through a Set
for letter in set("apple"):
    print(letter) # -> a p e l
```

|Method|Description|
|---|---|
|add()|	Adds an element to the set|
|clear()|	Removes all elements from the set|
|copy()|	Returns a copy of the set|
|difference()|	Returns the difference of two or more sets as a new set|
|difference_update()|	Removes all elements of another set from this set|
|discard()|	Removes an element from the set if it is a member. (Do nothing if the element is not in set)|
|intersection()|	Returns the intersection of two sets as a new set|
|intersection_update()|	Updates the set with the intersection of itself and another|
|isdisjoint()|	Returns True if two sets have a null intersection|
|issubset()|	Returns True if another set contains this set|
|issuperset()|	Returns True if this set contains another set|
|pop()|	Removes and returns an arbitrary set element. Raises KeyError if the set is empty|
|remove()|	Removes an element from the set. If the element is not a member, raises a KeyError|
|symmetric_difference()|	Returns the symmetric difference of two sets as a new set|
|symmetric_difference_update()|	Updates a set with the symmetric difference of itself and another|
|union()|	Returns the union of sets in a new set|
|update()|	Updates the set with the union of itself and others|

### Build-in functions with set

|Function|Description|
|---|---|
|all()|Returns True if all elements of the set are true (or if the set is empty).
|any()|Returns True if any element of the set is true. If the set is empty, returns False.
|enumerate()| an enumerate object. It contains the index and value for all the items of the set as a pair.
|len()|Returns the length (the number of items) in the set.
|max()|Returns the largest item in the set.
|min()|Returns the smallest item in the set.
|sorted()|Returns a new sorted list from elements in the set(does not sort the set itself).
|sum()|Returns the sum of all elements in the set.

### Dictionary

```python
# empty dictionary
my_dict = {}

# dictionary with integer keys
my_dict = {1: 'apple', 2: 'ball'}

# dictionary with mixed keys
my_dict = {'name': 'John', 1: [2, 4, 3]}

# using dict()
my_dict = dict({1:'apple', 2:'ball'})

# from sequence having each item as a pair
my_dict = dict([(1,'apple'), (2,'ball')
```

### Access elements
```python
# get vs [] for retrieving elements
my_dict = {'name': 'Jack', 'age': 26}

print(my_dict['name']) # -> Jack

print(my_dict.get('age')) # -> 26

# Trying to access keys which doesn't exist throws error
print(my_dict.get('address')) # -> None

print(my_dict['address']) # -> KeyError
```

### Changing and Adding Dictionary elements
```python
# update value
my_dict['age'] = 27

print(my_dict) # -> {'age': 27, 'name': 'Jack'}

# add item
my_dict['address'] = 'Downtown'

print(my_dict) # -> {'address': 'Downtown', 'age': 27, 'name': 'Jack'}
```

### Removing elements from Dictionary
```python
# create a dictionary
squares = {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# remove a particular item, returns its value
print(squares.pop(4)) # -> 16

print(squares) # -> {1: 1, 2: 4, 3: 9, 5: 25}

# remove an arbitrary item, return (key,value)
print(squares.popitem()) # -> (5, 25)

print(squares) # -> {1: 1, 2: 4, 3: 9}

# remove all items
squares.clear()

print(squares) # -> {}

# delete the dictionary itself
del squares

print(squares) # -> NameError: name 'squares' is not defined
```

### Python Dictionary Methods
|Method|Description|
|---|---|
|clear()|	Removes all items from the dictionary.|
|copy()|	Returns a shallow copy of the dictionary.|
|fromkeys(seq[, v])|	Returns a new dictionary with keys from seq and value equal to v (defaults to None).|
|get(key[,d])|	Returns the value of the key. If the key does not exist, returns d (defaults to None).|
|items()|	Return a new object of the dictionary's items in (key, value) format.|
|keys()|	Returns a new object of the dictionary's keys.|
|pop(key[,d])|	Removes the item with the key and returns its value or d if key is not found. If d is not provided and the key is not found, it raises KeyError.|
|popitem()|	Removes and returns an arbitrary item (key, value). Raises KeyError if the dictionary is empty.|
|setdefault(key[,d])|	Returns the corresponding value if the key is in the dictionary. If not, inserts the key with a value of d and returns d (defaults to None).|
|update([other])|	Updates the dictionary with the key/value pairs from other, overwriting existing keys.|
|values()|	Returns a new object of the dictionary's values|

```python
marks = {}.fromkeys(['Math', 'English', 'Science'], 0) # -> # Output: {'English': 0, 'Math': 0, 'Science': 0}

for item in marks.items():
    print(item)

print(list(sorted(marks.keys()))) # -> # Output: ['English', 'Math', 'Science']
```

### Python Dictionary Comprehension
```python
# Dictionary Comprehension
squares = {x: x*x for x in range(6)}
print(squares) # -> {0: 0, 1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# Dictionary Comprehension with if conditional
odd_squares = {x: x*x for x in range(11) if x % 2 == 1}
print(odd_squares) # -> {1: 1, 3: 9, 5: 25, 7: 49, 9: 81}
```

### Dictionary Membership Test
```python
# Membership Test for Dictionary Keys
squares = {1: 1, 3: 9, 5: 25, 7: 49, 9: 81}

print(1 in squares) # -> True

print(2 not in squares) # -> True

print(49 in squares) # -> False
```

### Iterating Through a Dictionary
```python
squares = {1: 1, 3: 9, 5: 25, 7: 49, 9: 81}
for i in squares: # -> iteration over keys
    print(squares[i])
```

### Build-in functions with dict
|Function|Description|
|---|---|
|all()|	Return True if all keys of the dictionary are True (or if the dictionary is empty).|
|any()|	Return True if any key of the dictionary is true. If the dictionary is empty, return False.|
|len()|	Return the length (the number of items) in the dictionary.|
|sorted()|	Return a new sorted list of keys in the dictionary.|

### <u>Python pipe library</u>

Library __pipe__ make it posible to use pipes ( | ) to apply multiple methods on an iterable.
```bash
pip install pipe
```

```python
from pipe import select, where, chain, groupby

arr = [1, 2, 3, 4, 5]
list(arr
    | where(lambda x: x % 2 == 0)
    | select(lambda x: x * 2))
```

__where - Filter elements in an Iterable__
```python
list(arr | where(lambda x: x % 2 == 0)) # -> [2, 4]
```

__select - Apply a Function to an Iterable__
```python
list(arr | select(lambda x: x * 2)) # -> [2, 4, 6, 8, 10]
```

__chain - Unfold Iterables__
```python
nested = [[1, 2, [3]], [4, 5]]
list(nested | chain) # -> [1, 2, [3], 4, 5]
```

__traverse - Traverse__
```python
list(nested | traverse) # -> [1, 2, 3, 4, 5]
```

__groupby - Group Elements__
```python
list(
    (1, 2, 3, 4, 5, 6, 7, 8, 9)
    | groupby(lambda x: "Even" if x % 2==0 else "Odd")
    | select(lambda x: {x[0]: list(x[1])})
) # -> [{'Even': [2, 4, 6, 8]}, {'Odd': [1, 3, 5, 7, 9]}]

list(
    (1, 2, 3, 4, 5, 6, 7, 8, 9)
    | groupby(lambda x: "Even" if x % 2==0 else "Odd")
    | select(lambda x: {x[0]: list(x[1] | where(lambda x: x > 2))})
) # -> [{'Even': [4, 6, 8]}, {'Odd': [3, 5, 7, 9]}]
```

__dedup - Deduplicate__
```python
arr = [1, 2, 2, 3, 4, 5, 6, 6, 7, 9, 3, 3, 1]
list(arr | dedup) # -> [1, 2, 3, 4, 5, 6, 7, 9]

list(
    data
    | dedup(key=lambda fruit: fruit["name"])
    | select(lambda fruit: fruit["count"])
    | where(lambda count: isinstance(count, int))
) #-> [2, 4]
```

__uniq() - Like dedup() but only deduplicate consecutive values, using the given key function if provided (or else the identity)__
```python
list([1, 1, 2, 2, 3, 3, 1, 2, 3] | uniq) # -> [1, 2, 3, 1, 2, 3]
```
__tee - outputs to the standard output and yield unchanged items, usefull for debugging__
```python
sum([1, 2, 3, 4, 5] | tee)
# -> 1
# -> 2
# -> 3
# -> 4
# -> 5
# -> 15
```

__take_while() - yields elements of the given iterable while the predicat is true__
```python
list([1, 2, 3, 4] | take_while(lambda x: x < 3)) # ->[1, 2]
```
__skip_while() - skips elements of the given iterable while the predicat is true, then yields others__
```python
list([1, 2, 3, 4] | skip_while(lambda x: x < 3)) # -> [3, 4]
```

__chain_with() - yields elements of the given iterable, then yields elements of its parameters__
```python
list((1, 2, 3) | chain_with([4, 5], [6])) # -> [1, 2, 3, 4, 5, 6]
```

__take() - yields the given quantity of the first elements of the given iterable.__
```python
list((1, 2, 3, 4, 5) | take(2)) # -> [1, 2]
```

__tail() - yields the given quantity of the last elements of the given iterable.__
```python
list((1, 2, 3, 4, 5) | tail(3)) # -> [3, 4, 5]
```

__skip() - Skips the given quantity of elements from the given iterable, then yields__
```python
list((1, 2, 3, 4, 5) | skip(2)) # -> [3, 4, 5]
```

__reverse__
```python
list([1, 2, 3] | reverse) # -> [3, 2, 1] 
```

__strip - Like Python's strip-method for str (also lstrip and rstrip).__
```python
'  abc   ' | strip # -> 'abc'
'.,[abc] ] ' | strip('.,[] ') # -> 'abc'
```

__permutations() - Returns all possible permutations__
```python
list('ABC' | permutations(2)) # -> [('A', 'B'), ('A', 'C'), ('B', 'A'), ('B', 'C'), ('C', 'A'), ('C', 'B')]
list(range(3) | permutations) # -> [(0, 1, 2), (0, 2, 1), (1, 0, 2), (1, 2, 0), (2, 0, 1), (2, 1, 0)]
```

__transpose() - Transposes the rows and columns of a matrix__
```python
[[1, 2, 3], [4, 5, 6], [7, 8, 9]] | transpose # -> [(1, 4, 7), (2, 5, 8), (3, 6, 9)]
```
    
__izip() - Just the itertools.izip__
```python
list((1, 2, 3, 4, 5, 6, 7, 8, 9) | izip([9, 8, 7, 6, 5, 4, 3, 2, 1])) 
# -> [(1, 9), (2, 8), (3, 7), (4, 6), (5, 5), (6, 4), (7, 3), (8, 2), (9, 1)]
```
    
   












### <u>Python File I/O</u>
### Opening Files in Python
```python
f = open("test.txt")    # open file in current directory
f.close()

# or

with open("test.txt") as f:
    pass
```
Open Mods

|Mode|Description|
|---|---|
|r|	Opens a file for reading. (default)|
|w|	Opens a file for writing. Creates a new file if it does not exist or truncates the file if it exists.|
|x|	Opens a file for exclusive creation. If the file already exists, the operation fails.|
|a|	Opens a file for appending at the end of the file without truncating it. Creates a new file if it does not exist.|
|t|	Opens in text mode. (default)|
|b|	Opens in binary mode.|
|+|	Opens a file for updating (reading and writing)|

```python
f = open("test.txt")      # equivalent to 'r' or 'rt'
f.close()

f = open("test.txt",'w')  # write in text mode
f.close()

f = open("img.bmp",'r+b') # read and write in binary mode
f.close()

f = open("test.txt", mode='r', encoding='utf-8')
f.close()
```

Open in try - block
```python
try:
   f = open("test.txt", encoding = 'utf-8')
   # perform file operations
finally:
   f.close()
```

Open with context manager
```python
with open("test.txt", encoding = 'utf-8') as f:
   # perform file operations

with open("test.txt",'w',encoding = 'utf-8') as f:
   f.write("my first file\n")
   f.write("This file\n\n")
   f.write("contains three lines\n")
```

Reading file
```python
f = open("test.txt",'r',encoding = 'utf-8')
f.read(4)    # read the first 4 data
'This'

f.read(4)    # read the next 4 data
' is '

f.read()     # read in the rest till end of file
'my first file\nThis file\ncontains three lines\n'

f.read()  # further reading returns empty sting

f.tell()    # get the current file position

f.seek(0)   # bring file cursor to initial position

# read file line by line
for line in f:
    print(line)

# Methon readline() reads a file till the newline
f.readline() # -> 'This is my first file\n'
f.readline() # -> 'This file\n'
f.readline() # -> 'contains three lines\n'
f.readline() # -> empty value
```
|Method|Description|
|---|---|
|close()|	Closes an opened file. It has no effect if the file is already closed.
|detach()|	Separates the underlying binary buffer from the TextIOBase and returns it.
|fileno()|	Returns an integer number (file descriptor) of the file.
|flush()|	Flushes the write buffer of the file stream.
|isatty()|	Returns True if the file stream is interactive.
|read(n)|	Reads at most n characters from the file. Reads till end of file if it is negative or None.
|readable()|	Returns True if the file stream can be read from.
|readline(n=-1)|	Reads and returns one line from the file. Reads in at most n bytes if specified.
|readlines(n=-1)|	Reads and returns a list of lines from the file. Reads in at most n bytes/characters if specified.
|seek(offset,from=SEEK_SET)|	Changes the file position to offset bytes, in reference to from (start, current, end).
|seekable()|	Returns True if the file stream supports random access.
|tell()|	Returns the current file location.
|truncate(size=None)|	Resizes the file stream to size bytes. If size is not specified, resizes to current location.
|writable()|	Returns True if the file stream can be written to.
|write(s)|	Writes the string s to the file and returns the number of characters written.
|writelines(lines)|	Writes a list of lines to the file.

### <u>Exception</u>

### Catching Exceptions
```python
try:
    # do something
    ...
    if a <= 0:
        raise ValueError("That is not a positive number!") # raise error
except ValueError as e: # Specific Exceptions
   # handle ValueError exception
   print(e)
except (TypeError, ZeroDivisionError): # Specific Exceptions
   # handle multiple exceptions
   # TypeError and ZeroDivisionError
except Exception as e: # Unspecific Exceptions
    print(e)
else: # if inside try everithing is well, then go to else
    # do something
finally: # this block will be execute no matter what
   # do something f.close()
```

### Custom Exception
```python
class CustomError(Exception):
    pass

# after that it is pasable to raise CustomError
raise CustomError

raise CustomError("An error occurred")
```

|Exception|	Cause of Error|
|---|---|
|AssertionError|	Raised when an assert statement fails.
|AttributeError|	Raised when attribute assignment or reference fails.
|EOFError|	Raised when the input() function hits end-of-file condition.
|FloatingPointError|	Raised when a floating point operation fails.
|GeneratorExit|	Raise when a generator's close() method is called.
|ImportError|	Raised when the imported module is not found.
|IndexError|	Raised when the index of a sequence is out of range.
|KeyError|	Raised when a key is not found in a dictionary.
|KeyboardInterrupt|	Raised when the user hits the interrupt key (Ctrl+C or Delete).
|MemoryError|	Raised when an operation runs out of memory.
|NameError|	Raised when a variable is not found in local or global scope.
|NotImplementedError|	Raised by abstract methods.
|OSError|	Raised when system operation causes system related error.
|OverflowError|	Raised when the result of an arithmetic operation is too large to be represented.
|ReferenceError|	Raised when a weak reference proxy is used to access a garbage collected referent.
|RuntimeError|	Raised when an error does not fall under any other category.
|StopIteration|	Raised by next() function to indicate that there is no further item to be returned by iterator.
|SyntaxError|	Raised by parser when syntax error is encountered.
|IndentationError|	Raised when there is incorrect indentation.
|TabError|	Raised when indentation consists of inconsistent tabs and spaces.
|SystemError|	Raised when interpreter detects internal error.
|SystemExit|	Raised by sys.exit() function.
|TypeError|	Raised when a function or operation is applied to an object of incorrect type.
|UnboundLocalError|	Raised when a reference is made to a local variable in a function or method, but no value has been bound to that variable.
|UnicodeError|	Raised when a Unicode-related encoding or decoding error occurs.
|UnicodeEncodeError|	Raised when a Unicode-related error occurs during encoding.
|UnicodeDecodeError|	Raised when a Unicode-related error occurs during decoding.
|UnicodeTranslateError|	Raised when a Unicode-related error occurs during translating.
|ValueError|	Raised when a function gets an argument of correct type but improper value.
|ZeroDivisionError|	Raised when the second operand of division or modulo operation is zero.

## <u>Best practice</u>

### <u>Unpacking</u>
```python
x, y, z = (12, 23, 34)
```
### <u>map</u>
Volumen berechnen, hierbei wir die erste Funktion auf alle nachfolgende Werte angewendet.
```python
x, y, z = map(int, input().strip().split())
print(f'Volume is {x * y * z}")


names = ['John ', ' Nonex ', '  Test']
names = map(str.strip, names)
```

### <u>reduce</u>
reduce(fun, list) - wird benutzt um aus einer Liste der Elemente eine Element zu bekommen, z. B. Summe, Max, Min

```python
import functools
 
# initializing list
lis = [1, 3, 5, 6, 2, ]
 
# using reduce to compute sum of list
print("The sum of the list elements is : ", end="")
print(functools.reduce(lambda a, b: a+b, lis))
 
# using reduce to compute maximum element from list
print("The maximum element of the list is : ", end="")
print(functools.reduce(lambda a, b: a if a > b else b, lis))
```

### <u>List comprehensions</u>
```python
# Ausdruck/Transformation for Element in Quelle if Bedinung
# Dieser Konstrukt [] {} oder in () stehen
# [] -> es entsteht eine Liste
# {} -> es entsteht ein Set oder Dict

# List
names = ['Max', 'Test', 'John', 'Sven', 'Tor'] 
names_start_t = [f'_{name}_' for name in names if name.startswith('T')]

# Set
names = ['Max', 'Test', 'John', 'Sven', 'Tor', 'Test'] 
names_start_t = {f'_{name}_' for name in names if name.startswith('T')}

# Dict
names = ['Max', 'Test', 'John', 'Sven', 'Tor', 'Test'] 
names_start_t = {index: f'_{name}_' for index, name in enumerate(names) if name.startswith('T')}

# Genexp -> Ergebnis dieser Operation ist ein Objekt und keine Datenstruktur
# dieses Objekt kann mit for - Loop iteriert werden oder es kann auf nächstes 
# Element mit next() zugegriffen werden.
names = ['Max', 'Test', 'John', 'Sven', 'Tor'] 
names_start_t_gen = (f'_{name}_' for name in names if name.startswith('T'))
# Genexp verfolg lazy - Prinzip, das heißt es wir nur dann Speicher beansprucht,
# wenn auf nächstes Element zugegriffen wird. Davor wir nur eine ein Objekt 
# angelet => geht sehr sparsam mit Speicher um 
```

### <u>Generator-Funktion</u>
yield - zeigt, das die Funktion ein Generator-Objekt zurückkommt. Dieses Objekt beinhaltet nicht die Daten, sondern die Logik wie die Daten erzeugt werden. Auf die Daten kann mit der Funktion _next()_ => _for-Loop_ zugegriffen werden. 

```python
def squares2():
    for e in range(0, 11, 2):
        yield e ** 2

# Generator-Funktion kann auch einen "return" beinhalten
```

### <u>Unboxing</u>
```python
# hierbei werden die Werte der linken Seite der Variablen der rechten Seite zugewiesen
a, b, c = [1, 2, 3]
a, b, c = (1, 2, 3)
a, b, c = 1, 2, 3
a, b, c = '123'

a, *b = [1, 2, 3] 
# => a = 1 und b = [2, 3]
# * - 1 in a und Rest in b
```
#### First and Last of iterable
```python
first, *_, last = [1,2,3,4,5,6,7] # => first = 1 and last = 7
```

### <u>Filter</u>
```python
names = ['Max', 'Test', 'John', 'Sven', 'Tor']
names_start_t = filter(lambda name: name.startswith('T', names))
```

### <u>Kopiere der Liste</u>
```python
indexes = [1, 2, 3]
another_indexes = [x for x in indexes] # zu lang
another_indexes = indexes[:] # alle Werte aus der alten Liste in neue Liste
```

### <u>Reverse der Liste</u>
```python
indexes = [1, 2, 3]
another_indexes = indexes[::-1] Liste
```

### <u>Prüfen ob alles True</u>
```python
if a and b and c and d:
    print('Ok')

# OR

if all(a,b,c,d):
    print('Ok')
```

### <u>Prüfen ob eins True</u>
```python
if a or b or c or d:
    print('Ok')

# OR

if any(a,b,c,d):
    print('Ok')
```

### <u>IF in line</u>
```python
color = 'green' if user.active else 'red'
```

### <u>Aufrufkonfiguration</u>
```python
if user.group == 'admin':
    process_admin_request(user, request)
elif user.group == 'manager':
    process_manager_request(user, request)
elif user.group == 'client':
    process_client_request(user, request)

ODER

group_to_method = {
    'admin': process_admin_request,
    'manager': process_manager_request,
    'client': process_manager_request
}

group_to_method[user.group](user, request)
```

### <u>Enumerate()</u>
```python
a = [1, 2, 3]

# enumerate returns index and value
for i, v in enumerate(a):
    pass
```

### <u>zip</u>
```python
a = [1, 2, 3]
b = [4, 5, 6]

# zip returns values of both lists
for av, bv in zip(a, b):
    pass
    
for i, (av, bv) in enumerate(zip(a, b)):
    pass
```

### <u>Timing</u>
```python
import time

start = time.perf_counter()
#do something
end = time.perf_counter()
print (end - start)
```

## <u>Unittest</u>
Bei der Erstellung der Unittest wird normalerweise eine neue Date erstellt, die einen *test_* prefix bekommt *test_{test file}.py*. In diese neue Datei wird zutestende Datei importiert

```python
import unittest
import {zu testende Datei}

class Test{Name}(unittest.TestCase):

    # jede Test-Methode muss mit test_ anfangen sonst wird es nicht als Test
    # vom Framework gesehen
    def test_{method_name}(self):
        assertEqual({call_method}, {right_return})

```

Starten der Tests
```bash
python -m unittest test_{name der Datei}.py
```

Wenn man die Datei mit Tests wie folgt erweitern:
```python
import unittest
import {zu testende Datei}

class Test{Name}(unittest.TestCase):

    # jede Test-Methode muss mit test_ anfangen sonst wird es nicht als Test
    # vom Framework gesehen
    def test_{method_name}(self):
        assertEqual({call_method}, {right_return})


if __name__ == "__main__":
    unittest.main()
```

dann kann die Datei wie gewohnt gestartet werden.

```bash
python test_{name der Datei}.py
```

|Method|Checks that|New in|
|---|---|---|
|assertEqual(a, b)|a == b||
|assertNotEqual(a, b)|a != b||
|assertTrue(x)|bool(x) is True||
|assertFalse(x)|bool(x) is False||
|assertIs(a, b)|a is b|3.1|
|assertIsNot(a, b)|a is not b|3.1|
|assertIsNone(x)|x is None|3.1|
|assertIsNotNone(x)|x is not None|3.1|
|assertIn(a, b)|a in b|3.1|
|assertNotIn(a, b)|a not in b|3.1|
|assertIsInstance(a, b)|isinstance(a, b)|3.2|
|assertNotIsInstance(a, b)|not isinstance(a, b)|3.2

Wenn man bei mehreren Tests z. B. man testet eine Klasse, jede Test-Methode mit dem Anlegen eines Objektes anfängt. Dann kann man diese Zeile auslagern. Es gibt Methoden

```python
def setUp(self):
    pass

def tearDown(self):
    pass
```
die namen sollen genau so geschrieben werden. Die Methode ```setUp(self)``` wird am Anfang jeden Test gestartet. Die Methode ```tearDown(self)``` wird am Ende jeden Test gestartet.

Außerdem kann man am Anfang aller Tests und am Ende aller Tests bestimmten Code ausführen lassen. Dafür muss man folgende Methoden anlegen

```python
@classmethod
def setUpClass(cls):
    pass

@classmethod
def tearDown(cls):
    pass
```

## <u>REGex with Python</u>

### <u>Python Main Functions</U>
__re.match()__
+ Matcht am Anfang eines Strings
+ Achtung: Das gilt auch in Multiline-Mode
+ Rückgabewert: MatchObject | None

re.match(r'pattern', string, flags=0)

|__Flags__||
|---|---
|re.IGNORECASE	|Ignoriert Klein- und Großschreibung
|re.MULTILINE	|Integriert alle Zeilen, nicht nur die erste
|re.DOALL	    |Erweitert „.“ Auf neue Zeilen (\n)
|re.UNICODE	    |Erweiter {\w, \W, \b, \B} auf Unicode
|re.VERBODE	    |Erlaubt Kommentare in dem regulären Ausdruck
|Mehrfach Auswahl möglich, über den \| - Pipe-Operator.

__re.fullmatch()__
+ Matcht den gesamten String
+ Rückgabewert: MatchObject | None

    re.fullmatch(r'pattern', string, flags=0)

__re.search()__
+ Matcht an dem ersten Vorkommen eines Musters im String
+ Rückgabewert: MatchObject | None

    re.search(r'pattern', string, flags=0)

__matchObject.group()__
+ Ermöglicht den Zugriff auf den Inhalt einer oder mehrere Gruppen des MatchObjects
+ Gruppen starten bei (1), in Gruppe (0) steht kompletter Match
+ Rückgabewert: String

__matchObject.groups()__
+ Zeigt alle inhalte der Gruppen an
+ Rückgabewert: Liste

__re.sub()__
+ Das gematchte Muster wird durch einen definierten Ersatzstring ersetzt
+ Rückgabewert: Vollständiger String mit ersetztem/überschriebenen Inhalt

re.sub(r'pattern', 'repl', string, counter=0, flags=0)
+ Pattern – gesuchter Muster
+ Repl – durch was wird das Gefundene ersetzt
+ String – text in dem nach Muster gesucht wird
+ Counter – wie oft soll das Ersetzen stattfinden

__re.findall()__
+ Scannt den String von links nach rechts und wirft die Matches in der Reihenfolge des Vorkommens zurück
+ Rückgabewert: Liste mit allen Matches

    re.findall(r'pattern', string, flags=0)

__re.finditer()__
+ Erzeugt einen Iterator in der Höhe der Anzahl aller gefundener Matches
+ Rückgabewert: Callable Iterator
re.finditer(r'pattern', string, flags=0)

__re.split()__
+ Teilt den String an der Stelle an des das Muster gematcht wird.
+ Rückgabewert: Liste mit Strings

    re.split(r'pattern', string, flags=0)

# <u>WSL2</u>

->suchen in Windows nach _"Windows Feature"_. In dem Fenster _Windows-Subsystem for Linux_ & _Virtual Machine Platform_ anhacken.

[Download OS](https://docs.microsoft.com/de-de/windows/wsl/install-manual)

Die .appx - Datein in .zip umbennen und zip - Datei öffnen. Von dort die .exe starten.
Erst nach der Installation soll Docker installiert werden. In Dockereinstellungen kann dann WSL2 und Docker Zusammenarbeit einstellen.

# <u>Big O</u>

    - O(1) -> const time
    - O(log n) -> binary search
    - O(n) -> search element in Array
    - O(n log n) -> search algorithm (Quicksort, - mergsort, heapsort)
    - O(n²) -> for in for, sort algorithm
    - O(2^n)
    - O(n!)

# <u>Cmd</u>

# <u>REGex</u>

||_Anchors_|
| --- | --- |
|^	|Anfang des Strings oder der Zeile
|\A	|Anfang des Strings oder der Zeile
|$	|Ende des Strings oder der Zeile
|\Z	|Ende des Strings oder der Zeile
|\b	|Wortgrenze
|\B	|Keine Wortgrenze
|\<	|Anfang des Wortes
|\>	|Ende des Wortes


||_Special Sequences_|
| --- | --- |
|.	|Jedes Zeichen, bis auf neue Zeile \n
|\s	|Weißraum (Leerzeichen, Tabs)
|\S	|Kein Weißraum
|\d	|Zahlen
|\D	|Keine Zahlen
|\w	|Worte (Buchstaben und Zahlen)
|\W	|Keine Worte


|       |_Quantifiers_      |
| ---   | ---               |
|*	    |0 oder mehr
|+	    |1 oder mehr
|?	    |0 oder 1
|{3}	|Genau 3
|{3,}	|3 oder mehr
|{3,5}	|3 bis 5
|       |Mit "?" Non-Greedy.


||_Sets, Ranges & Groups_|
| --- | --- |
|[abc]	|Set beinhaltet (a or b or c)
|[^abc]	|Set beinhaltet nicht (a or b or c)
|a-z	|Range - Kleinbuchstaben von a bis z
|A-Z	|Range - Großbuchstaben von A bis Z
|0-9	|Range Zahlen 0 bis 9
|(...)	|(Capturing) Gruppe
|(a\|b)	|a oder b
|(?:...)|Passive (non-capturing) Gruppe

<br>

_Special Characters_
|   |   |   |
|---|---|---|
|^	|[	|]
|+	|{	|}
|*	|(	|)
|\|	|<	|>
|$	|?	|\
|.	|	|

Escape Sequences: \	- Escape "Special Characters"

_String replacements_

* Verkürzt den RegEx-Ausdruck
* Reduziert Redundanzen im RegEx
* Verifizieren gewollte Wiederholungen

Wenn man für einen Ausdruck eine Gruppe erstellt (\d\d\d\d) dann besteht die Möglichkeit an einer anderen Stelle auf die Gruppe zu referenzieren mit \1 wenn es die erste Gruppe in dem Ausdruck war. 
r“^(\d\d\d\d)\.\1\.\1“ => z. B.: 1234.1234.1234
in dem Fall referenziert \1 auf die Gruppe (\d\d\d\d)

_Benannte Gruppen_

Standardmäßig sind Gruppen unbenannt. Sie werden automatisch von 1 aufsteigen benannt. Bei einer Vielzahl von Gruppen kann das unübersichtlich werden. In dem Fall können benannte Gruppen helfen. Als Gruppenname kann jeder String gewählt werden.

r“^(?P\<Zahl\>\d\d\d)\_\1\_\d{4}$“ -> matchObj.group(„Zahl“)

||_Assertions_|
| --- | --- |
|?=	| Lookahead assertion
|?!	| Negative lookahead
|?<=| Lookbehind assertion
|?>	| Once-only Subexp¬ression
|?!= or ?<!	| Negative lookbehind
|?()| Condition [if then]
|?()| Condition [if then else]
|?#	| Kommentar

Defeniere Regeln im Muster. 

Lookahead (?=) – Matcht ein definiertes Muster nur, wenn ein weiteres definiertes Muster darauf folgt.

Negative lookahead (?!) – Matcht ein definiertes Muster nur, wenn ein weiteres definiertes Muster _NICHT_ darauf folgt.

Lookbehind (?<=) - Matcht ein definiertes Muster nur, wenn ein weiteres definiertes Muster vorhergeht.

Negative lookbehind (?<!) - Matcht ein definiertes Muster nur, wenn ein weiteres definiertes Muster NICHT vorhergeht.

_Conditionals_
+	Wenn-Dann-Sonst Statement
+	(?(WENN A) DANN B |SONST C) 
+	Der SONST und der DANN Blöcke sind Optional
    +	(?(WENN) DANN)
    +	(?(WENN)|SONST)

# <u>Git</u>
![git_merkblatt_01](.\git_merkblatt_01.jpg)
![git_merkblatt_02](.\git_merkblatt_02.jpg)

<hr/>

## Zum Nachschlagen

### [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

### [LaTeX Formeln](https://www.grund-wissen.de/informatik/latex/mathematischer-formelsatz.html)