# Lib and cLib

* StringIO and cStringIO — Work with text buffers using file-like API

  ```python
  try:
      from cStringIO import StringIO
  except ImportError:
      from StringIO import StringIO
  ```

* pickle and cPickle — Python object serialization

  ```python
  try:
     import cPickle as pickle
  except ImportError:
     import pickle
  ```

  ​
