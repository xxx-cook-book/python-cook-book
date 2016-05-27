# Lambda

##  Sorted

```python
In [19]: a = {'Huang': ['Kimi', 1988], 'Li': ['Robbin', 1968]}

In [20]: # Order By Year

In [23]: sorted(a.iteritems(), key=lambda(k, v): v[1])
Out[23]: [('Li', ['Robbin', 1968]), ('Huang', ['Kimi', 1988])]
    
In [24]: sorted(a.iteritems(), key=lambda x: x[1][1])
Out[24]: [('Li', ['Robbin', 1968]), ('Huang', ['Kimi', 1988])]
    
In [25]: # Order By (Name, Year)
    
In [26]: sorted(a.iteritems(), key=lambda(k, v): (v[0], v[1]))
Out[26]: [('Huang', ['Kimi', 1988]), ('Li', ['Robbin', 1968])]

In [27]: sorted(a.iteritems(), key=lambda x: (x[1][0], x[1][1]))
Out[27]: [('Huang', ['Kimi', 1988]), ('Li', ['Robbin', 1968])]
```

## Multi Sort

Python has a stable sort. So it's safe to sort one by one.

```python
In [30]: list1 = sorted(a.iteritems(), key=lambda x: x[1][0], reverse=True)

In [31]: list1 = sorted(list1, key=lambda x: x[1][1], reverse=False)
```

## References

[1] half full@StackOverflow, [Sorting a Python list by two criteria](http://stackoverflow.com/questions/5212870/sorting-a-python-list-by-two-criteria)