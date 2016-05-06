# Circular Imports

## About

* a.py

  ```shell
  # -*- coding: utf-8 -*-

  from b import add

  def minus(a, b):
      return a - b

  if __name__ == '__main__':
      print add(1, 2)
  ```

* b.py

  ```python
  # -*- coding: utf-8 -*-

  from a import minus

  def add(a, b):
      return a + b

  if __name__ == '__main__':
      print minus(2, 1)
  ```

* exec

  ```shell
  $ python a.py
  Traceback (most recent call last):
    File "a.py", line 3, in <module>
      from b import add
    File "/Users/xxx/b.py", line 3, in <module>
      from a import minus
    File "/Users/xxx/a.py", line 3, in <module>
      from b import add
  ImportError: cannot import name addxxxxxxxxxx 
  ```

## Solution
* a.py

  ```shell
  # -*- coding: utf-8 -*-

  def minus(a, b):
      return a - b

  if __name__ == '__main__':
      from b import add
      print add(1, 2)
  ```

* b.py

  ```python
  # -*- coding: utf-8 -*-

  def add(a, b):
      return a + b

  if __name__ == '__main__':
      from a import minus
      print minus(2, 1)
  ```


* exec

  ```shell
  $ python a.py
  3
  $ python b.py
  1
  ```



