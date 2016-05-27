# copy

The difference between shallow and deep copying is only relevant for compound objects (objects that contain other objects, like lists or class instances):

- A *shallow copy* constructs a new compound object and then (to the extent possible) inserts *references* into it to the objects found in the original.
- A *deep copy* constructs a new compound object and then, recursively, inserts *copies* into it of the objects found in the original.

```python
In [1]: import copy

In [2]: a = [1, 2, 3, ['a', 'b', 'c']]

In [3]: b = a

In [4]: c = copy.copy(a)

In [5]: d = copy.deepcopy(a)

In [6]: a, b, c, d
Out[6]:
([1, 2, 3, ['a', 'b', 'c']],
 [1, 2, 3, ['a', 'b', 'c']],
 [1, 2, 3, ['a', 'b', 'c']],
 [1, 2, 3, ['a', 'b', 'c']])

In [7]: a.append(4)

In [8]: a[3].append('d')

In [9]: a, b, c, d
Out[9]:
([1, 2, 3, ['a', 'b', 'c', 'd'], 4],
 [1, 2, 3, ['a', 'b', 'c', 'd'], 4],
 [1, 2, 3, ['a', 'b', 'c', 'd']],
 [1, 2, 3, ['a', 'b', 'c']])
```

## dict.copy()

*help(dict.copy)*

```python
Help on method_descriptor:

copy(...)
    D.copy() -> a shallow copy of D
```

*Examples:*

```python
In [1]: dt = {'a': 1, 'b': {'c': 3}}

In [2]: dt1 = dt.copy()

In [3]: dt1
Out[3]: {'a': 1, 'b': {'c': 3}}

In [4]: dt['c'] = 3

In [5]: dt1
Out[5]: {'a': 1, 'b': {'c': 3}}

In [6]: dt['b']['d'] = 4

In [7]: dt1
Out[7]: {'a': 1, 'b': {'c': 3, 'd': 4}}
```

## References

[1] Docs@Python, [8.17. copy — Shallow and deep copy operations](https://docs.python.org/2/library/copy.html)