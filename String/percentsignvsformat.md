# % vs format

## format

_New in version 2.6._

See [Format String Syntax](https://docs.python.org/2/library/string.html#formatstrings) for a description of the various formatting options that can be specified in format strings.

This method of string formatting is the new standard in Python 3, and should be preferred to the `%` formatting described in[String Formatting Operations](https://docs.python.org/2/library/stdtypes.html#string-formatting) in new code.

```python
In [1]: '{}{}'.format(1, 2)
Out[1]: '12'

In [2]: '{0}{1}{0}'.format(1, 2)
Out[2]: '121'

In [3]: '{one}{two}'.format(one=1, two=2)
Out[3]: '12'

In [2]: '{one}{two}{one}'.format(one=1, two=2)
Out[2]: '121'

In [4]: '{{_}}{one}{two}'.format(one=1, two=2)
Out[4]: '{_}12'

In [5]: '{_}{one}{two}'.format(one=1, two=2)
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
<ipython-input-5-85a872d71e8b> in <module>()
----> 1 '{_}{one}{two}'.format(one=1, two=2)
KeyError: '_'
```

## %s

```python
In [7]: '%s%s' % (1, 2)
Out[7]: '12'
```

## UnicodeEncodeError

```python
In [1]: '{}{}'.format('test', u'测试')
---------------------------------------------------------------------------
UnicodeEncodeError                        Traceback (most recent call last)
<ipython-input-1-507ab7ed13b6> in <module>()
----> 1 '{}{}'.format('test', u'测试')
UnicodeEncodeError: 'ascii' codec can't encode characters in position 0-1: ordinal not in range(128)

In [2]: u'{}{}'.format('test', u'测试')
Out[2]: u'test\u6d4b\u8bd5'

In [3]: '%s%s' % ('test', u'测试')
Out[3]: u'test\u6d4b\u8bd5'

In [4]: from __future__ import unicode_literals

In [5]: '{}{}'.format('test', u'测试')
Out[5]: u'test\u6d4b\u8bd5'
```

* [Python: Using .format() on a Unicode-escaped string](http://stackoverflow.com/questions/3235386/python-using-format-on-a-unicode-escaped-string)

## References

[1] PyFormat@TT4IT, [PyFormat —— Using % and .format() for great good!](http://tt4it.com/resources/discuss/2074/)