# Web-Zwischenspeicher
Web-Zwischenspeicher developed with C++ maintains the Cache of a browser.The Cache Memory is implemented using Splay trees to handle Cache efficiently. Loading and Searching of URL is implemented with Bloom Filters to make the process efficient.

# Bloom Filters
Bloom filter is a probabilistic data structure invented by Burton Howard Bloom in 1970. It allows for membership check-in constant space and time. Bloom filter trades exactness for efficiency and has a large number of applications in software engineering.
 ## Some of the properties of bloom filters are:
  1. It allows for membership lookup in constant space & time. Bloom filter can very quickly answer YES/NO questions, like “is this item in the set?”.
  2. Very infrequently it will give a false positive answer, implies it will say YES if the answer is NO (Probably in the set).
  3. It will never give false negative answer implies it will never say NO if the answer is YES (Definitely not in the set).
  4. The basic bloom filter supports two operations test and add.
  5. It has constant time complexity for both adding items and asking whether a key is present or not.
  6. You can’t remove an item from a bloom filter.
  7. It also requires very less space compared to the number of items you need to store and check.
  8. Bloom filters use hash functions and before discussing bloom filter in detail, let’s have a look at hashing and hash functions.
 ## Hashing and Hash Functions  
  A hash is like a fingerprint of your data. A hash function takes input data which can be of any length and gives back output as an identifier of smaller, fixed length. The identifier can be used to index or compare or identify data.
  
  Most hash functions are one-way operations, which means you can get an identifier from the data, not vice versa. Two-way hash functions also exist, but they are not particularly useful.
  
 # Important properties of hash functions are:
  * Same input must always have the same output. It is one of the most important features.
  * The output values should be uniformly distributed. It means each possible output value should be equally likely.
  * The output should be distributed randomly. A Similar input should not give similar output.
  * Each input should give a unique output to minimize the number of collisions.
  * It should be fast.
 
 Different hash functions are designed for different tasks. Their properties differ based on the task for which you are using them. 
 
 # Hash functions used with bloom filter should have the following properties:
  * It should be fast.
  * The hash function should have rare collisions and hash value should be evenly and randomly distributed.
  
 ## Bloom filter implementation
 A basic bloom filter will have two operations **test** and **add.** The Base data structure for the bloom filter is **bit vector** or **bit-array.** It uses a bit array of size **m** and **k** hash functions. Initially, all the bits in bit vector will be set to 0.

_**To add an element to the bloom filter, we hash the element k times using hash functions and set bits at indexes of those hash values.**_

 
 ```python3
 def add(item):
    for hash_function in hash_functions:
        index = hash_function(item) % m
        bit_array[index] = True
 ```
  
 
 To test for membership, we simply hash the element with hash functions and then check if those indices are set in the bit vector. If the bit at all those indices is not set, you know that the element is not in the set. If they are set, it might be because the same element or combination of other elements could have set the same bits. Later is the reason why a bloom filter can sometimes give a **false positive** answer.
 

```python3
def test(item):
   results = []
   for hash_function in hash_functions:
       index = hash_function(item) % m
       if bit_array[index]:
           results.append(True)
       else:
           results.append(False)
   return reduce(lambda a, b : a & b, results)  
```
