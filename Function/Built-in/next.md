# next

_New In Python 2.6_

```python
next(iterator[, default])
```

Retrieve the next item from the *iterator* by calling its [`next()`](https://docs.python.org/2/library/stdtypes.html#iterator.next) method. If *default* is given, it is returned if the iterator is exhausted, otherwise [`StopIteration`](https://docs.python.org/2/library/exceptions.html#exceptions.StopIteration) is raised.

## Idiomatic

```python
a = -1
for i in range(1, 10):
    if not i % 4:
        a = i
        break
```

to

```python
next((i for i in range(1, 10) if not i % 4), -1)
```

## References

[1] Docs@Python, [2. Built-in Functions — next(iterator[, default])](https://docs.python.org/2/library/functions.html#next)

