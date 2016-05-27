# collections

*New In Python 2.4*

## Counter

*New In Python 2.7*

A [`Counter`](https://docs.python.org/2/library/collections.html#collections.Counter) is a [`dict`](https://docs.python.org/2/library/stdtypes.html#dict) subclass for counting hashable objects. It is an unordered collection where elements are stored as dictionary keys and their counts are stored as dictionary values. Counts are allowed to be any integer value including zero or negative counts. The [`Counter`](https://docs.python.org/2/library/collections.html#collections.Counter) class is similar to bags or multisets in other languages.

```python
In [1]: import collections

In [2]: c = collections.Counter('Hello Python!')

In [3]: c
Out[3]:
Counter({' ': 1,
         '!': 1,
         'H': 1,
         'P': 1,
         'e': 1,
         'h': 1,
         'l': 2,
         'n': 1,
         'o': 2,
         't': 1,
         'y': 1})
```

* TopN

  ```python
  In [4]: c.most_common()
  Out[4]:
  [('l', 2),
   ('o', 2),
   ('!', 1),
   (' ', 1),
   ('e', 1),
   ('H', 1),
   ('n', 1),
   ('P', 1),
   ('t', 1),
   ('h', 1),
   ('y', 1)]

  In [5]: c.most_common(3)
  Out[5]: [('l', 2), ('o', 2), ('!', 1)]
  ```

* -TopN

  ```python
  In [6]: c.most_common()[:-2-1:-1]
  Out[6]: [('y', 1), ('h', 1)]
  ```

* Remove Zero and Negative Counts

  ```python
  In [7]: c = collections.Counter({'a': 1, 'b': 0, 'c': -1})

  In [8]: c
  Out[8]: Counter({'a': 1, 'b': 0, 'c': -1})

  In [9]: c += collections.Counter()

  In [10]: c
  Out[10]: Counter({'a': 1})
  ```

## OrderedDict

*New In Python 2.7*

Ordered dictionaries are just like regular dictionaries but they remember the order that items were inserted. When iterating over an ordered dictionary, the items are returned in the order their keys were first added.

```python
In [11]: items = (
   ....:     ('A', 1),
   ....:     ('B', 2),
   ....:     ('C', 3)
   ....: )

In [12]: dict(items)
Out[12]: {'A': 1, 'B': 2, 'C': 3}

In [13]: collections.OrderedDict(items)
Out[13]: OrderedDict([('A', 1), ('B', 2), ('C', 3)])

In [14]: print _12
{'A': 1, 'C': 3, 'B': 2}

In [15]: print _13
OrderedDict([('A', 1), ('B', 2), ('C', 3)])

In [16]: for k, v in _12.iteritems():
   ....:     print k, v
   ....:
A 1
C 3
B 2

In [17]: for k, v in _13.iteritems():
   ....:     print k, v
   ....:
A 1
B 2
C 3
```

## References

[1] Docs@Python, [8.3. collections — High-performance container datatypes](https://docs.python.org/2/library/collections.html)

