# Modify Characters In String

```python
In [1]: py = 'Hello Pytlon!'

In [2]: import array

In [3]: a = array.array('c', py)

In [4]: a[9] = 'h'

In [5]: a
Out[5]: array('c', 'Hello Python!')

In [6]: a.tostring()
Out[6]: 'Hello Python!'
    
In [7]: b = array.array('u', u'你好，Pytlon')

In [8]: b[6] = u'h'

In [9]: b
Out[9]: array('u', u'\u4f60\u597d\uff0cPython')

In [10]: b.tounicode()
Out[10]: u'\u4f60\u597d\uff0cPython'

In [11]: print b.tounicode()
你好，Python
```

