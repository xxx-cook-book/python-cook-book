# Import From Parent Folder

## Search Path

When a module named `spam` is imported, the interpreter first searches for a built-in module with that name. If not found, it then searches for a file named `spam.py` in a list of directories given by the variable [`sys.path`](https://docs.python.org/2/library/sys.html#sys.path). [`sys.path`](https://docs.python.org/2/library/sys.html#sys.path) is initialized from these locations:

- the directory containing the input script (or the current directory).
- [`PYTHONPATH`](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (a list of directory names, with the same syntax as the shell variable `PATH`).
- the installation-dependent default.

After initialization, Python programs can modify [`sys.path`](https://docs.python.org/2/library/sys.html#sys.path). The directory containing the script being run is placed at the beginning of the search path, ahead of the standard library path. This means that scripts in that directory will be loaded instead of modules of the same name in the library directory. This is an error unless the replacement is intended. See section [Standard Modules](https://docs.python.org/2/tutorial/modules.html#tut-standardmodules) for more information.

## Directory Tree

```shell
$ tree importtests
importtests
├── common
│   ├── __init__.py
│   ├── aaa.py
└── function
    ├── __init__.py
    └── bbb.py
```

* aaa.py

  ```python
  $ cat common/aaa.py
  def say_hi():
      print 'Python Cook Book'
  ```

* bbb.py

  ```python
  $ cat function/bbb.py
  from common.aaa import say_hi

  say_hi()
  ```

* Exec

  ```shell
  $ python bbb.py
  Traceback (most recent call last):
    File "bbb.py", line 14, in <module>
      from common.aaa import say_hi
  ImportError: No module named common.aaa
  ```

## Solution No.1

```python
$ cat function/bbb.py
import sys
sys.path.append('..')

from common.aaa import say_hi

say_hi()
```

* Exce in ``function`` dir

  ```shell
  $ python bbb.py
  Python Cook Book
  ```

* Exec in ``importtests`` dir

  ```shell
  $ python function/bbb.py
  Traceback (most recent call last):
    File "function/bbb.py", line 12, in <module>
      from common.aaa import say_hi
  ImportError: No module named common.aaa
  ```

## Solution No.2

Use 3rd Libray [path.py](https://github.com/jaraco/path.py)

```python
$ cat function/bbb.py
import path
import sys

folder = path.path(__file__).abspath()
sys.path.append(folder.parent.parent)

from common.aaa import say_hi

say_hi()
```

* Installation

  ```shell
  pip install path.py
  ```

* Exce in ``function`` dir

  ```shell
  $ python bbb.py
  Python Cook Book
  ```

* Exec in ``importtests`` dir

  ```shell
  $ python function/bbb.py
  Python Cook Book
  ```

## Solution No.3

Use Standard Libray ``os.path``

```python
$ cat function/bbb.py
import os
import sys

root_folder = os.path.abspath(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root_folder)

from common.aaa import say_hi

say_hi()
```

* Exce in ``function`` dir

  ```shell
  $ python bbb.py
  Python Cook Book
  ```

* Exec in ``importtests`` dir

  ```shell
  $ python function/bbb.py
  Python Cook Book
  ```

## Solution No.4

Use ``explicit relative import``

```python
$ cat function/bbb.py
# from .. common.aaa import say_hi  # Or As Below
from ..common.aaa import say_hi

say_hi()
```

* Exec in ``importtests' parent`` dir

  ```shell
  $ python -m importtests.function.bbb
  Python Cook Book

  $ python -m importtests.function.bbb.py
  Python Cook Book
  /Users/xxx/venv/bin/python: No module named importtests.function.bbb.py
  ```

## APPEND or INSERT

* sys.path.append(folder.parent.parent)
* sys.path.insert(0, folder.parent.parent)
  * Recommendation

## References

[1] Docs@Python, [6. Modules — 6.1.2. The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)

[2] jaraco@Github, [path.py — "Path" object conveniently wrapping assorted file/path-related functionality](https://github.com/jaraco/path.py)