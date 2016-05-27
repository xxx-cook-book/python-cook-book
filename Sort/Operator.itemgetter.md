# Operator.itemgetter

_New In Python 2.4_

_Changed in version 2.5: Added support for multiple item extraction._

## Operator.itemgetter

`operator.``itemgetter`(*item*)

`operator.``itemgetter`(**items*)

Return a callable object that fetches *item* from its operand using the operand’s [`__getitem__()`](https://docs.python.org/2/library/operator.html#operator.__getitem__) method. If multiple items are specified, returns a tuple of lookup values. For example:

- After `f = itemgetter(2)`, the call `f(r)` returns `r[2]`.
- After `g = itemgetter(2, 5, 3)`, the call `g(r)` returns `(r[2], r[5], r[3])`.

Equivalent to:

```python
def itemgetter(*items):
    if len(items) == 1:
        item = items[0]
        def g(obj):
            return obj[item]
    else:
        def g(obj):
            return tuple(obj[item] for item in items)
    return g
```

The items can be any type accepted by the operand’s [`__getitem__()`](https://docs.python.org/2/library/operator.html#operator.__getitem__) method. Dictionaries accept any hashable value. Lists, tuples, and strings accept an index or a slice:

```python
>>> itemgetter(1)('ABCDEFG')
'B'
>>> itemgetter(1,3,5)('ABCDEFG')
('B', 'D', 'F')
>>> itemgetter(slice(2,None))('ABCDEFG')
'CDEFG'
```

##  Sorted

```python
In [19]: a = {'Huang': ['Kimi', 1988], 'Li': ['Robbin', 1968]}

In [20]: # Order By Year

In [21]: import operator

In [22]: sorted(a.iteritems(), key=lambda(k, v): operator.itemgetter(1)(v))
Out[22]: [('Li', ['Robbin', 1968]), ('Huang', ['Kimi', 1988])]

In [23]: # Order By (Name, Year)

In [24]: sorted(a.iteritems(), key=lambda(k, v): operator.itemgetter(0, 1)(v))
Out[24]: [('Huang', ['Kimi', 1988]), ('Li', ['Robbin', 1968])]
```

## Multi Sort

Python has a stable sort. So it's safe to sort one by one.

```python
In [33]: list1 = sorted(a.iteritems(), key=lambda(k, v): operator.itemgetter(0)(v))

In [34]: list1 = sorted(list1, key=lambda(k, v): operator.itemgetter(1)(v))
```

## References

[1] Docs@Python, [9.9. operator — Standard operators as functions](https://docs.python.org/2/library/operator.html)

[2] half full@StackOverflow, [Sorting a Python list by two criteria](http://stackoverflow.com/questions/5212870/sorting-a-python-list-by-two-criteria)