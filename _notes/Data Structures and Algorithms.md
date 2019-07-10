---
layout : page
title: Data Structures and Algorithms

---



**Time-complexity Analysis**

1. Types of complexity
2. Order
3. Complexity of some common tasks

**Data Structures**

1. Arrays
2. Linked List
3. Stacks
4. Queues
5. Graphs
6. Trees

**Algorithms**

1. Sorting
2. Searching
3. Recursion 
4. Backtracking
5. Dynamic Programming


**Hash Tables**
- data are stored in an associative manner (in key, value format)
- uses a hashing function that generates a slot or an index to store/insert any element or value

```python
#Simplest implementation
hash_table = [None]*10
print(hash_table)

def hashing_function(key):
  return key % len(hash_table)
                        
def insert(hash_table, key, value):
  hash_key = hashing_function(key)
  hash_table[hash_key] = value

insert(hash_table, 10, 'Nepal')
print (hash_table)
# Output: 
# ['Nepal', None, None, None, None, None, None, None, None, None]

insert(hash_table, 25, 'USA')
print (hash_table)
# Output: 
# ['Nepal', None, None, None, None, 'USA', None, None, None, None]    
```



---
