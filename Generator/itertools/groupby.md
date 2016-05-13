# groupby

```python
itertools.groupby(iterable[, key])
```

## Warning

* sorted the data using the same key function 

  The operation of `groupby()` is similar to the `uniq` filter in Unix. It generates a break or new group every time the value of the key function changes (which is why it is usually necessary to have **sorted the data using the same key function**). That behavior differs from SQL’s GROUP BY which aggregates common elements regardless of their input order.

## Example

* Question

  * Input

    ```python
    [{'lv1': 1, 'lv2': 2, 'name': 'table1'},
     {'lv1': 1, 'lv2': 2, 'name': 'table2'},
     {'lv1': 1, 'lv2': 2, 'name': 'table3'},
     {'lv1': 1, 'lv2': 3, 'name': 'table3'},
     {'lv1': 1, 'lv2': 3, 'name': 'table5'},
     {'lv1': 2, 'lv2': 1, 'name': 'table1'},
     {'lv1': 2, 'lv2': 1, 'name': 'table2'}]
    ```

  * Output

    ```python
    [{'lv1': 1, 'lv2': 2, 'name': ['table1', 'table2', 'table3']},
     {'lv1': 1, 'lv2': 3, 'name': ['table3', 'table5']},
     {'lv1': 2, 'lv2': 1, 'name': ['table1', 'table2']}]
    ```

* Answer

  ```python
  In [3]: import itertools

  In [4]: nodes = [{'lv1': 1, 'lv2': 2, 'name': 'table1'},
     ...:  {'lv1': 1, 'lv2': 2, 'name': 'table2'},
     ...:  {'lv1': 1, 'lv2': 2, 'name': 'table3'},
     ...:  {'lv1': 1, 'lv2': 3, 'name': 'table3'},
     ...:  {'lv1': 1, 'lv2': 3, 'name': 'table5'},
     ...:  {'lv1': 2, 'lv2': 1, 'name': 'table1'},
     ...:  {'lv1': 2, 'lv2': 1, 'name': 'table2'}]

  In [5]: map(lambda x : {'lv1': x[0][0], 'lv2' : x[0][1], 'name': [y['name'] for y in x[1]]}, itertools.groupby(nodes, lambda x : (x['lv1'], x['lv2'])))
  Out[5]:
  [{'lv1': 1, 'lv2': 2, 'name': ['table1', 'table2', 'table3']},
   {'lv1': 1, 'lv2': 3, 'name': ['table3', 'table5']},
   {'lv1': 2, 'lv2': 1, 'name': ['table1', 'table2']}]
  ```

## References

[1] Docs@Python, [9.7. itertools — Functions creating iterators for efficient looping](https://docs.python.org/2/library/itertools.html#itertools.groupby)

