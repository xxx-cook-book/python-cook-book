# functools

_New In Python 2.5_

## partial

`functools.partial`(*func[,\*args][, **keywords]*)

Return a new [`partial`](https://docs.python.org/2/library/functools.html#functools.partial) object which when called will behave like *func* called with the positional arguments *args* and keyword arguments *keywords*.

The [`partial()`](https://docs.python.org/2/library/functools.html#functools.partial) is used for partial function application which “freezes” some portion of a function’s arguments and/or keywords resulting in a new object with a simplified signature. For example, [`partial()`](https://docs.python.org/2/library/functools.html#functools.partial) can be used to create a callable that behaves like the [`int()`](https://docs.python.org/2/library/functions.html#int) function where the *base* argument defaults to two:

```python
>>> from functools import partial
>>> basetwo = partial(int, base=2)
>>> basetwo.__doc__ = 'Convert base 2 string to an int.'
>>> basetwo('10010')
18
```

## update_wrapper

## wraps

## total_ordering

_New In Python 2.7_

Given a class defining one or more rich comparison ordering methods, this class decorator supplies the rest. This simplifies the effort involved in specifying all of the possible rich comparison operations:

The class must define one of [`__lt__()`](https://docs.python.org/2/reference/datamodel.html#object.__lt__), [`__le__()`](https://docs.python.org/2/reference/datamodel.html#object.__le__), [`__gt__()`](https://docs.python.org/2/reference/datamodel.html#object.__gt__), or [`__ge__()`](https://docs.python.org/2/reference/datamodel.html#object.__ge__). In addition, the class should supply an [`__eq__()`](https://docs.python.org/2/reference/datamodel.html#object.__eq__) method.

```python
In [70]: @total_ordering
   ....: class Student:
   ....:         def __eq__(self, other):
   ....:                 return ((self.lastname.lower(), self.firstname.lower()) ==
   ....:                         (other.lastname.lower(), other.firstname.lower()))
   ....:         def __lt__(self, other):
   ....:                 return ((self.lastname.lower(), self.firstname.lower()) <
   ....:                         (other.lastname.lower(), other.firstname.lower()))
   ....:

In [71]: print dir(Student)
['__doc__', '__eq__', '__ge__', '__gt__', '__le__', '__lt__', '__module__']
```

## References

[1] Docs@Python, [9.8. functools — Higher-order functions and operations on callable objects](https://docs.python.org/2/library/functools.html)

