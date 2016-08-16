# Compat

```python
# -*- coding: utf-8 -*-

"""
pythoncompat
"""

import sys

# -------
# Pythons
# -------

# Syntax sugar.
_ver = sys.version_info

#: Python 2.x?
is_py2 = (_ver[0] == 2)

#: Python 3.x?
is_py3 = (_ver[0] == 3)

# ---------
# Specifics
# ---------

if is_py2:
    range = xrange

    builtin_str = str
    bytes = str
    str = unicode
    basestring = basestring
    numeric_types = (int, long, float)

elif is_py3:
    range = range

    builtin_str = str
    str = str
    bytes = bytes
    basestring = (str, bytes)
    numeric_types = (int, float)
```

* Usage

  ```python
  from .compat import range, builtin_str, str, bytes, basestring, numeric_types
  ```

## References
[1] kennethreitz/requests, [requests/requests/compat.py](https://github.com/kennethreitz/requests/blob/master/requests/compat.py)