# Python

## Lists

```py
# Indexing
l =  [0,  1,  2,  3,  4,  5]
# P:  0   1   2   3   4   5
# N: -6  -5  -4  -3  -2  -1

# Slicing
# l[START_INCLUDED : END_NOT_INCLUDED : STEP]

# Positive Slicing
print(l[0:2]) # 0, 1
# Negative Slicing
print(l[-3:-1]) # 3, 4
# Step
print(l[0:4:2]) # 0, 2

# Concatenation
print(l + [6]) # [0, 1, 2, 3, 4, 5, 6]
# Replication
print([1, 2] * 2) # [1, 2, 1, 2]
# Deletion
del l[2] # [0, 1, 3, 4, 5]

# Loop
for x in [7, 8, 9]:
  print(ex)
'''
7
8
9
'''
# Loop enumerated
for i, x in enumerate([7, 8, 9]):
  print(i, x)
'''
0 7
1 8
2 9
'''

# Insert
l.insert(1, 999) # [0, 999, 1, 2, ...]
# Append
l.append(999) # [0, ..., 999]

# Sort
l = [2, 3, 1, 6]
## Ascending
l.sort() # [1, 2, 3, 6]
## Descending
l.sort(reverse = True) # [6, 3, 2, 1]
# Returns a new sorted list
sorted(l, [reverse])
```

## Sets
```py
# Equivalent way to define an UNSORTED collection of UNIQUE values
s = {1, 1, 2, 2, 3} # 1, 2, 3
s = set([1, 1, 2, 2, 3]) # 1, 2, 3
s = {1, 1, 2, 2, 3} # 1, 2, 3

# Add element(s)
a.add(6)
a.update([5, 6, 7])

# Remove element
a.remove(6) # RAISE error if 6 not in a
a.discard(6) # QUIET -> No raise error if 6 not in a

# Operations
a, b = set([1, 2, 3]), set([3, 4, 5])
## Union "|"
print(a | b) # set([1, 2, 3, 4, 5])
## Intersection "&"
print(a & b) # set([3])
## Difference "-"
print(a - b) # set([1, 2])
## Symmetric Difference "^"
print(a ^ b) # set([1, 2, 4, 5])
```

## Comprehension
```py
# List
l = [0, 1, 2]
[x + 1 for x in l] # [1, 2, 3]

# Set
s = {0, 1, 2}
set([x + 1 for x in s]) # set(1, 2, 3)

# Dict
d = { "zero": 0, "one": 1, "two": 2 }
{ k: v+1 for k, v in d.items() }
```

## Lambda
```py
# Anonymous function
double = lambda a: a * 2
double(3) # 6

l = [1, 2, 3]
list(map(double, l)) # [2, 4, 6]
```

## Dictionaries
```py
d = { "mon": 1, "tue": 2, "wed": 3 }

# These can be used in for loops for many things
d.keys() # ["mon", "tue", "wed"]
d.values() # [1, 2, 3]
d.items() # [("mon": 1), ("tue": 2), ("wed": 3)]

# Update in batch
d.update({ "mon": 0, "thu": 4 })
print(d) # { "mon": 0, "tue": 2, "wed": 3, "thu": 4 }
```

## Stacks
```py
# LIFO - Using lists
s = []
s.append(2)
s.append(3)
s.pop() # 3
```

## Queues
```py
# FIFO - Through library
from queue import Queue

q = Queue([maxsize=0])

# Size handling
q.empty()
q.full()
q.qsize()
# Operations
q.put(10)
q.put(12)
q.get() # 10 -- get_nowait is the no-wat version for empty queue
```

## Useful built-in
```py
# Get input from user
print("Inser an int")
num = int(input())

# ASCII code
ord("A") # 65
ord("a") # 97

# Dict (takes whatever list/tuple of 2 elements)
dict([("one", 1, 3), ("two", 2)]) # {"one": 1, "two": 2}

# Range (creates an iterable list of numbers)
# (start [included], end [not included], step)
range(0, 4) # [0, 1, 2, 3]
range(0, 4, 2) # [0, 2]
range(3, -1, -1) # [3, 2, 1, 0]

# Zip
a = ["a", "b", "c"]
b = [1, 2, 3]
list(zip(a, b)) # [('a', 1), ('b', 2), ('c', 3)]
```

## Date and Time
```py
```

## Args, Kwargs
```py
```

## Global
```py
# Modify a global value from inside a function
def func():
  global value
  value = "Local"

value = "Global"
func()
print(value) # Local
```

## Exception handling
```py
def divide(a, den):
  try:
    return a / den
  except ZeroDivisionError as e:
    print('Div by 0')
  except Exception as e:
    print('Another error:', e)
  finally:
    print('Always printed')
```

## Math
```py
# Integer div
5 // 2 # 2
# Normal div
3 / 2 # 1.5

# Modulo
3 % 2 # 1

# Power
2 ** 3 # 8
math.pow(2, 3) # 8.0
```

## Strings
```py
```

## Regex
```py
```

## Virtualenv
```sh
pip install virtualenv

cd MyProject

# Create a new venv (inherit global installed packages)
virtualenv venv --system-site-packages

# Activate the venv (for each terminal used inside the project)
source venv/bin/activate

# Install all the local dependencies (make sure "(venv)" is in your prompt)
pip install <package>

# Remember to gitignore it
echo "venv/" >> .gitignore

# Deactivate the venv
deactivate

## Note: for better handling of multiple projects use virtualenvwrapper
## It setups all virtual environments in ~/.virtualenv
pip install virtualenvwrapper
```
