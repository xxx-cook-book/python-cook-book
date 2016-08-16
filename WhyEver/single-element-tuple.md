# Single Element Tuple

## Phenomena

```python
In [18]: (3 + 4)
Out[18]: 7

In [19]: (3 + 4, )
Out[19]: (7,)
```

## Reason

```python
In [20]: (3 + 4) * 5
Out[20]: 35
    
or

In [21]: (3 + 4) * 5
Out[21]: (7, 7, 7, 7, 7)
```

## References

[1] Bugs@Python, [Make Python create a tuple with one element in a clean way](http://bugs.python.org/issue2817)