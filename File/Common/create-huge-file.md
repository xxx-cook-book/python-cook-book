# Create Huge File

```python
In [1]: with open('large.csv', 'wb') as f:
   ...:     f.seek(1073741824 - 1)
   ...:     f.write('\0')
   ...:

In [2]: import os

In [3]: os.stat('large.csv').st_size
Out[3]: 1073741824
```

