# \_\_future\_\_

```python
In [5]: from __future__ import
CO_FUTURE_ABSOLUTE_IMPORT   absolute_import
CO_FUTURE_DIVISION          all_feature_names
CO_FUTURE_PRINT_FUNCTION    division
CO_FUTURE_UNICODE_LITERALS  generators
CO_FUTURE_WITH_STATEMENT    nested_scopes
CO_GENERATOR_ALLOWED        print_function
CO_NESTED                   unicode_literals
_Feature                    with_statement
```

## absolute_import

Forbidden ``implicit relative import``, Not Forbidden ``explicit relative import``

* See [Import From Parent Folder](../../Import/ImportFromParentFolder.md)

## unicode_literals

```python
# still running on Python 2.7

from __future__ import unicode_literals

print '\'xxx\' is unicode?', isinstance('xxx', unicode)
print 'u\'xxx\' is unicode?', isinstance(u'xxx', unicode)
print '\'xxx\' is str?', isinstance('xxx', str)
print 'b\'xxx\' is str?', isinstance(b'xxx', str)
```

***<u>Outputs</u>***

```python
'xxx' is unicode? True
u'xxx' is unicode? True
'xxx' is str? False
b'xxx' is str? True
```

***<u>Problems</u>***

* Python 2.x ***<u>&</u>*** Without unicode_literals

  ```python
  Python 2.7.8 (default, Dec 11 2015, 13:09:06)
  Type "copyright", "credits" or "license" for more information.

  IPython 4.0.1 -- An enhanced Interactive Python.
  ?         -> Introduction and overview of IPython's features.
  %quickref -> Quick reference.
  help      -> Python's own help system.
  object?   -> Details about 'object', use 'object??' for extra details.

  In [1]: from datetime import datetime

  In [2]:

  In [2]: now = datetime.now()

  In [3]: print now.strftime('%m月%d日 %H:%M')
  05月17日 11:22
  ```

* Python 2.x ***<u>&</u>*** With unicode_literals

  ```python
  In [4]: from __future__ import unicode_literals

  In [5]: from datetime import datetime

  In [6]:

  In [6]: now = datetime.now()

  In [7]: print now.strftime('%m月%d日 %H:%M')
  ---------------------------------------------------------------------------
  UnicodeEncodeError                        Traceback (most recent call last)
  <ipython-input-7-765bdd22665e> in <module>()
  ----> 1 print now.strftime('%m月%d日 %H:%M')

  UnicodeEncodeError: 'ascii' codec can't encode character u'\u6708' in position 2: ordinal not in range(128)
  ```

* Python 3.x

  ```python
  Python 3.4.1 (default, Dec 11 2015, 12:11:12)
  Type "copyright", "credits" or "license" for more information.

  IPython 4.0.1 -- An enhanced Interactive Python.
  ?         -> Introduction and overview of IPython's features.
  %quickref -> Quick reference.
  help      -> Python's own help system.
  object?   -> Details about 'object', use 'object??' for extra details.

  In [1]: from datetime import datetime

  In [2]:

  In [2]: now = datetime.now()

  In [3]: print(now.strftime('%m月%d日 %H:%M'))
  05月17日 11:22
  ```

***<u>Reasons</u>***

* ``Strftime`` accept string param in Python 2.x, when pass unicode, ``strftime``  will convert it.

***<u>Solutions</u>***

* Solution No.1 — Runtime Encoding

  ```python
  In [8]: from __future__ import unicode_literals

  In [9]: import sys

  In [10]: from datetime import datetime

  In [11]:

  In [11]: reload(sys)
  <module 'sys' (built-in)>

  In [12]: sys.setdefaultencoding('utf-8')

  In [13]:

  In [13]: now = datetime.now()

  In [14]: print now.strftime('%m月%d日 %H:%M')
  05月17日 11:22
  ```

* Solution No.2 — Use Byte String

  ```python
  In [15]: from __future__ import unicode_literals

  In [16]: from datetime import datetime

  In [17]:

  In [17]: now = datetime.now()

  In [18]: print now.strftime(b'%m月%d日 %H:%M')  # Appointed Bytearray String
  05月17日 11:22

  In [19]:

  In [19]: # Method Below Also Is OK

  In [20]: t = bytearray('%m月 %d %H:%M', 'utf-8')

  In [21]: print now.strftime(str(t))
  05月 17 11:22
  ```

## References

[1] Docs@Python, [28.11. __future__ — Future statement definitions](https://docs.python.org/2/library/__future__.html)