# more_itertools

## Installation

```shell
pip install more_itertools
```

## Usage

- Yield unique elements, preserving order

  ```python
  In [2]: from  more_itertools import unique_everseen
  In [3]: items = [1, 3, 2, 4, 5, 7, 6, 8, 1, 3, 2, 4, 5, 7, 6, 8]
  In [4]: list(unique_everseen(items))
  Out[4]: [1, 3, 2, 4, 5, 7, 6, 8]
  ```

## References

[1] erikrose@Github, [More Itertools — More routines for operating on iterables, beyond itertools](https://github.com/erikrose/more-itertools)