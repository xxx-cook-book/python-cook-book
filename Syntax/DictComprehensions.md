# Dict Comprehensions

_New In Python 2.7 and 3.0_

## Example

* Question

  * Input

    ```python
    {'a': ['1', '2', '2'], 'b': ['4', '4', '5', '5']}
    ```

  * Output

    ```python
    {'a': ['1', '2'], 'b': ['4', '5']}
    ```

* Answer

  ```python
  In [1]: from more_itertools import unique_everseen

  In [2]: nodes = {'a': ['1', '2', '2'], 'b': ['4', '4', '5', '5']}

  In [3]: {k: list(unique_everseen(v)) for k, v in nodes.iteritems()}
  Out[3]: {'a': ['1', '2'], 'b': ['4', '5']}
  ```

## References

[1] PEPS@Python Developer's Guide, [PEP 274 -- Dict Comprehensions](https://www.python.org/dev/peps/pep-0274/)

[2] The Python Tutorial@Python Docs, [5. Data Structures — 5.5. Dictionaries](https://docs.python.org/2.7/tutorial/datastructures.html?highlight=comprehensions#dictionaries)

