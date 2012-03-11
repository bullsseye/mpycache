
# -----------------------------------------------------------------------------------
#   mpycache - a LRU Cache implementation in python
#   author: Saurav Mohapatra (mohaps@gmail.com)
#   website: http://code.google.com/p/mpycache
#   version: 1.1.0
#   date: 03/10/2012
#   license: Apache License 2.0
#   (http://www.apache.org/licenses/LICENSE-2.0.html)
# ------------------------------------------------------------------------------------


*mpycache* is a handy [http://en.wikipedia.org/wiki/Cache_algorithms#Least_Recently_Used Least Recently Used (LRU) Cache] implementation in python that supports max entry count and max age of entry semantics. Additionally one can specify the elasticity of the cache (i.e. how much over the max size limit can one go before the cache is pruned down to max size and oldest entries are removed.

*mpycache* uses the [http://www.apache.org/licenses/LICENSE-2.0.html Apache License 2.0]

The usage is pretty straight-forward. instantiate a cache with maxSize, maxAge in milliseconds and elasticity and you can use the put(key,value) and get(key) to use it. additionally a clear() method is provided that clears the cache, an erase(key) method to remove a particular key if present and has_key(key) method to check if a key is in the cache.

Set maxSize = 0 to disable size checks and maxAgeMillis = 0 to disable age check.

example usage:

from mpycache import LRUCache;

maxSize = 10; # after pruning cache will come down to 10 elements
maxAgeMillis = 0.3; # we only hold entries for 300 usecs
elasticity = 3; # the cache will at most have 10+3=13 elements
lc = LRUCache(maxSize, maxAgeMillis, elasticity);
lc.put('somekey', 'somevalue');
print 'val : %s' % (lc.get('somekey'));



*mpycache* was written by someone who has written a fair bit of C/C++/Java/Python code (enterprise grade and in production) and *does* understand that semicolons are not needed at the end of every statement in python. You can either go all snooty pythonista on this non-issue or just take mpycache for a spin. :)

