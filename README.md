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
  1. A hash is like a fingerprint of your data. 
  2. A hash function takes input data which can be of any length and gives back output as an identifier of smaller, fixed length. 
  3. The identifier can be used to index or compare or identify data.
