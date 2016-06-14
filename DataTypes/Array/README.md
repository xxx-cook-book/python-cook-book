# Array

``List`` vs ``Tuple`` vs ``Array``

## Standard Library

```python
from array import array
```

## 3rd Library

* Installation

  ```shell
  pip install numpy
  ```

* Usage

  ```python
  >>> import numpy as np
  >>> a = np.arange(15).reshape(3, 5)
  >>> a
  array([[ 0,  1,  2,  3,  4],
         [ 5,  6,  7,  8,  9],
         [10, 11, 12, 13, 14]])
  >>> a.shape
  (3, 5)
  >>> a.ndim
  2
  >>> a.dtype.name
  'int64'
  >>> a.itemsize
  8
  >>> a.size
  15
  >>> type(a)
  <type 'numpy.ndarray'>
  >>> b = np.array([6, 7, 8])
  >>> b
  array([6, 7, 8])
  >>> type(b)
  <type 'numpy.ndarray'>
  ```

  * More Examples See: [Quickstart tutorial](https://docs.scipy.org/doc/numpy-dev/user/quickstart.html)

## References

[1] Numpy@TT4IT, [Numpy — the fundamental package for scientific computing with Python.](http://tt4it.com/resources/discuss/945/)

[2] Docs@Python, [8.6. array — Efficient arrays of numeric values](https://docs.python.org/2/library/array.html)