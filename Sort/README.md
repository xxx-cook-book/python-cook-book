# Sort

## ``sort()`` vs ``sorted()``

```python
In [1]: a = [1, 3, 2, 4, 5, 7, 6, 8]

In [2]: sorted(a)
Out[2]: [1, 2, 3, 4, 5, 6, 7, 8]

In [3]: a
Out[3]: [1, 3, 2, 4, 5, 7, 6, 8]

In [4]: a.sort()

In [5]: a
Out[5]: [1, 2, 3, 4, 5, 6, 7, 8]
```

* Python has a stable sort. So it's safe to sort one by one.

## References

[1] Wikis@Python, [Sorting Mini-HOW TO](https://wiki.python.org/moin/HowTo/Sorting/)