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

List Concatenation and Replication:
When we merge the contents of 2 lists into one list, it is called list concatenation.

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

### Sets
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

### Comprehension
```py
```

### Strings
```py
```

### Regex
```py
```

### Lambda
```py
```

### Dictionaries
```py
```

### Stack
```py
```

### Date and Time
```py
```

### Args, Kwargs
```py
```

### Global
```py
# Modify a global value from inside a function
def func():
  global value
  value = "Local"

value = "Global"
func()
print(value) # Local
```

### Exception handling
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

### Math
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
