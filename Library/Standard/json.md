# json

```python
In [1]: import json

In [2]: {1: 'a'}
Out[2]: {1: 'a'}

In [3]: json.dumps(_2)
Out[3]: '{"1": "a"}'

In [4]: json.loads(_3)
Out[4]: {u'1': u'a'}
```

## References

[1] Docs@Python, [18.2. json — JSON encoder and decoder](https://docs.python.org/2/library/json.html)