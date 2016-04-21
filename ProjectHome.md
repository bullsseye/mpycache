**mpycache** is a handy [Least Recently Used (LRU) Cache](http://en.wikipedia.org/wiki/Cache_algorithms#Least_Recently_Used) implementation in python that supports max entry count and max age of entry semantics. Additionally one can specify the elasticity of the cache (i.e. how much over the max size limit can one go before the cache is pruned down to max size and oldest entries are removed.

**mpycache** uses the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

I wrote this to scratch my own itch and to use in a **real** project. :) It's all implemented in a single python file [mpycache.py](http://code.google.com/p/mpycache/source/browse/trunk/mpycache.py) that you can drop into your project and start using right away. You can also download the file [here](http://code.google.com/p/mpycache/downloads/list)


The usage is pretty straight-forward. instantiate a cache with maxSize, maxAge in milliseconds and elasticity and you can use the put(key,value) and get(key) to use it. additionally a clear() method is provided that clears the cache, an erase(key) method to remove a particular key if present and has\_key(key) method to check if a key is in the cache.

Set maxSize = 0 to disable size checks and maxAgeMillis = 0 to disable age check.

example usage:
```
from mpycache import LRUCache as LRUCache;

maxSize = 10; # after pruning cache will come down to 10 elements
maxAgeMillis = 0.3; # we only hold entries for 300 usecs
elasticity = 3; # the cache will at most have 10+3=13 elements
lc = LRUCache(maxSize, maxAgeMillis, elasticity);
lc.put('somekey', 'somevalue');
print 'val : %s' % (lc.get('somekey'));
```



**mpycache** was written by someone who has written a fair bit of C/C++/Java/Python code (enterprise grade and in production) and **does** understand that semicolons are not needed at the end of every statement in python. You can either go all [snarky](http://irclogs.jackgrigg.com/text.pl?server=irc.freenode.net;channel=buildbot;date=2011-05-11) [pythonista](http://zaphodb.soup.io/post/195674892/bin-env-python) on this _non-issue_ or just take mpycache for a spin. :)