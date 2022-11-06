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

## Heap / Priority Queue

### Basics
```py
import heapq

q = [5, 7, 9, 1, 3]
# Heap conversion (optional, you can start with empty list and through pop/push keeping a clean heap)
heapq.heapify(q)     # [1, 3, 9, 7, 5]
heapq.heappush(q, 4) # [1, 3, 4, 7, 5, 9]
heapq.heappop(q)     # 1
print(q)             # [3, 5, 4, 7, 9]
```
### Note
- Only implemented through MinHeap
  - For MaxHeap, easy hack: negative number can be used and multiplying by `-1` before returning
- By default the library take the **first element** of the tuple as the cost

```py
import heapq

cost = 10
node = 0
neighbours = [1, 2, 5]

# Init
q = [(cost, source, neighbours)]
# OR
q = []
heapq.heappush(q, (cost, source, neighbours))

# Pop
cost, n, neighs = heapq.heappop(q)
```

### Sorting
```py
from dataclasses import dataclass
from heapq import heappop, heappush, heapify

@dataclass
class Process:
  start: int
  end: int
  load: int

  # Sort process by end time, used by heapq
  def __lt__(self, other):
    return self.end < other.end

  def __repr__(self):
    return f"<{self.start},{self.end},{self.load}>"

procs = [
  Process(0, 4, 6),
  Process(5, 7, 10),
  Process(2, 3, 2)
]

# For sort, use the key param
procs.sort(key=lambda x: x.end)
# [<2,3,2>, <0,4,6>, <5,7,10>]

heapify(procs)
# [<2,3,2>, <0,4,6>, <5,7,10>]
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

# min, max, sum, any, all
min([1, 2, 3]) # 1
max([1, 2, 3]) # 3
sum([1, 2, 3]) # 6
any(map(lambda x: x > 0, [-1, -2, 3])) # True
all(map(lambda x: x > 0, [-1, -2, 3])) # False
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
# Basics
a = "Hello"
a.upper() # 'HELLO'
a.lower() # 'hello'
a.isupper() # False
a.islower() # False

# Join and split
l = ["one", "two", "three"]
s = ",".join(l) # "one,two,three"
s.split(",") # ["one", "two", "three"]
```

## Args, Kwargs
```py
# Multiple args, can be used as "rest" def test(x, y, *argv)
def test(*argv):
  print(argv)

def testk(**kwargs):
  print(dict(kwargs.items()))

test(1, 2) # [1, 2]
testk(one = 1, two = 2) # {"one": 1, "two": 2}
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
