# zip

_New In Python 2.0_

```python
zip([iterable, ...])
```

## Example

```python
In [1]: for x, y in [1, 2], [3, 4]:
   ...:     print x, y
   ...:     
1 2
3 4

In [2]: for x, y in zip([1, 2], [3, 4]):
    print x, y
   ...:     
1 3
2 4
```

## References

[1] Docs@Python, [2. Built-in Functions — zip([iterable, ...])](https://docs.python.org/2/library/functions.html#zip)

