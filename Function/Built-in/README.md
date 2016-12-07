# Built-in

## ``__builtin__``

This module provides direct access to all ‘built-in’ identifiers of Python; for
example, `__builtin__.open` is the full name for the built-in function
[`open()`](https://docs.python.org/2/library/functions.html#open).

* [28.3. ``__builtin__`` — Built-in objects](https://docs.python.org/2/library/__builtin__.html)

## ``builtins``

This module provides direct access to all ‘built-in’ identifiers of Python; for
example, `builtins.open` is the full name for the built-in function
[`open()`](https://docs.python.org/3/library/functions.html#open).

* [29.3. ``builtins`` — Built-in objects](https://docs.python.org/3/library/builtins.html)

## ``__builtins__``

## compat

```python
if is_py2:
    import __builtin__
    builtins = __builtin__

elif is_py3:
    import builtins
    builtins = builtins
```
* Usage

  ```python
  from .compat import builtins

  builtins.open
  ```
