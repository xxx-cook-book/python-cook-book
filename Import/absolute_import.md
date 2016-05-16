# absolute_import

As described in  [PEP 8 -- Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/#imports)

```
Implicit relative imports should never be used and have been removed in Python 3.
```

And ``absolute_import`` was used to Forbidden ``implicit relative import``, Not Forbidden ``explicit relative import``

## Usage

```python
from __future__ import absolute_import
```


## References

[1] PEPS@Python Developer's Guide, [PEP 328 -- Imports: Multi-Line and Absolute/Relative](https://www.python.org/dev/peps/pep-0328/)