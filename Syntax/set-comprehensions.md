# Set Comprehensions

Similarly to [list comprehensions](https://docs.python.org/2/tutorial/datastructures.html#tut-listcomps), set comprehensions are also supported:

```python
>>> a = {x for x in 'abracadabra' if x not in 'abc'}
>>> a
set(['r', 'd'])
```

## Syntax

```python
{expr for iter_var in iterable}
{expr for iter_var in iterable if cond_expr}
```

## References

[1] PEPS@Python Developer's Guide, [PEP 218 -- Adding a Built-In Set Object Type](https://www.python.org/dev/peps/pep-0218/)

[2] Docs@Python, [5. Data Structures — 5.4. Sets](https://docs.python.org/2/tutorial/datastructures.html#sets)