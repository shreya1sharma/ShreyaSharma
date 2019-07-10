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
- Collision: occurs when two items/values get the same slot/index, i.e. the hashing function generates same slot number for multiple items
- Collision resolution techniques
    - Linear Probing - search another empty slot; starts sequentialy through the slots until an empty slot is encountered. The movement is in circular fashion.
    - Chaining - allowing multiple items to exist in the same slot, create a chain/collection of items in a single slot

```python
#Chaining Implementation : use nested list in hash table
hash_table = [[] for _ in range(10)]
print(hash_table)
# Output: 
# [[], [], [], [], [], [], [], [], [], []]

#use append() in insert function
def insert(hash_table, key, value):
  hash_key = hashing_function(key)
  hash_table[hash_key].append(value)
insert(hash_table, 10, 'Nepal')
insert(hash_table, 25, 'USA')
insert(hash_table, 20, 'India')
print (hash_table)
# Output: 
# [['Nepal', 'India'], [], [], [], [], ['USA'], [], [], [], []]

```

- hash(): In-built python function to create a hash value of any key
- creates an integer hash value for both string and integer key. The hash value for integer will be same as it is, i.e. hash(10) will be 10, hash(20) will be 20, and so on.

```python
hash_key = hash('10')
print (hash_key) # Output: 6272037681056609
 
hash_key = hash(10)
print (hash_key) # Output: 10
```

- Standard Implementation of 3 methods : insert, search, delete

```python
#Creating a hash table
hash_table = [[] for _ in range(10)]

#insert function
def insert(hash_table, key, value):
  hash_key = hash(key) % len(hash_table) # hash_key creates a slot for key
  key_exists = False
  bucket = hash_table(hash_key) #sub-list
  for i, kv in enumerate(bucket):
     k, v = kv
     if key == k:
        key_exists = True
        break
   if key_exists:
      bucket[i] = ((key, value))
   else:
      bucket.append((key, value))
 
insert(hash_table, 10, 'Nepal')
insert(hash_table, 25, 'USA')
insert(hash_table, 20, 'India')
print (hash_table)
# Output:
# [[(10, 'Nepal'), (20, 'India')], [], [], [], [], [(25, 'USA')], [], [], [], []]
  
#search function
def search(hash_table, key):
  hash_key = hash(key) % len(hash_table)
  bucket = hash_table[hash_key]
  for i, kv in enumerate(bucket):
    k, v = kv
    if key == k:
       return v

print (search(hash_table, 10)) # Output: Nepal
print (search(hash_table, 20)) # Output: India
print (search(hash_table, 30)) # Output: None
  
#delete function
def delete(hash_table, key, value):
  hash_key = hash(key) % len(hash_table) # hash_key creates a slot for key
  key_exists = False
  bucket = hash_table(hash_key) #sub-list
  for i, kv in enumerate(bucket):
     k, v = kv
     if key == k:
        key_exists = True
        break
   if key_exists:
      del bucket[i]
      print ('Key {} deleted'.format(key))
   else:
      print ('Key {} not found'.format(key))
```
- keywords: key -> hashing function -> hash value -> index/slot -> hash table -> data value
---
