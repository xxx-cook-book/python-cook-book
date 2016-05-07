# yield

## yield

```python
In [30]: def yield1():
   ....:     yield 10
   ....:     yield 9
   ....:

In [32]: [y for y in yield1()]
Out[32]: [10, 9]
```

## recursion

```python
In [34]: def yield2(a):
   ....:     yield a
   ....:     if a > 0:
   ....:         for i in yield2(a - 1):
   ....:             yield i
   ....:

In [35]: [y for y in yield2(10)]
Out[35]: [10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

## yield from

_New In Python 3.3_

```python
In [36]: def yield3(a):
   ....:     yield a
   ....:     yield from yield3(a - 1) if a > 0 else ''
   ....:

In [37]: [y for y in yield3(10)]
Out[37]: [10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

In Python 2.x or Before Python 3.3, will raise ``SyntaxError``

```python
In [2]: def yield3(a):
   ...:     yield a
   ...:     yield from yield3(a - 1) if a > 0 else ''
   ...:
  File "<ipython-input-2-f3544a53b65c>", line 3
    yield from yield3(a - 1) if a > 0 else ''
             ^
SyntaxError: invalid syntax
```

## References

[1] Docs@Python, [What’s New In Python 3.3](https://docs.python.org/3/whatsnew/3.3.html)