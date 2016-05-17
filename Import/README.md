# Import

## Directory Tree

```shell
$ tree importtests
importtests
├── common
│   ├── __init__.py
│   ├── aaa.py
└── function
    ├── __init__.py
    ├── bbb.py
    └── ccc.py
```

## Import

Import ``bbb `` in ``ccc.py`` 

| Import                  | Description               | Python 2.x  | Python 3.x  |
| :---------------------- | ------------------------- | ----------- | ----------- |
| import bbb              | Implicit Relative Imports | Deprecation | Removed     |
| from . import bbb       | Explicit Relative Imports | Acceptable  | Acceptable  |
| from functon import bbb | Absolute Imports          | Recommended | Recommended |

* Implicit Relative Imports  Removed In Python 3.x

  * bbb.py

    ```python
    $ cat common/bbb.py
    def say_hi():
        print 'Python Cook Book'
    ```

  * ccc.py

    ```python
    $ cat common/ccc.py
    import bbb

    bbb.say_hi()
    ```

  * Python 2.x

    ```python
    $ python
    Python 2.7.8 (default, Dec 11 2015, 13:09:06)
    [GCC 4.2.1 Compatible Apple LLVM 5.1 (clang-503.0.40)] on darwin
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import importtests.function.ccc
    Hello Python
    ```

  * Python 3.x

    ```python
    $ python
    Python 3.4.1 (default, Dec 11 2015, 12:11:12)
    [GCC 4.2.1 Compatible Apple LLVM 5.1 (clang-503.0.40)] on darwin
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import importtests.function.ccc
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
      File "/Users/fuwenlan/Brightcells/importtests/function/ccc.py", line 4, in <module>
        import bbb
    ImportError: No module named 'bbb'
    ```

## References

[1] PEPS@Python Developer's Guide, [PEP 8 -- Style Guide for Python Code — Imports](https://www.python.org/dev/peps/pep-0008/#imports)