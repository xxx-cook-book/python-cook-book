# Split Every N Character

##  Bank Card

```python
def bank_card(self, message, n=4, fill=' ', strip=False):
    """
    Format bank card, split every n character, n default 4.
    :param message:
    :param n:
    :param fill:
    :param strip:
    :return:
    """
    return fill.join(re.findall(r'.{1,%s}' % (n, ), re.sub(r'\s+', '', message) if strip else message))
```

* Usage

  ```python
  In [2]: bank_card('6225xxxxxxxxxxxx')
  Out[2]: '6225 xxxx xxxx xxxx'

  In [3]: bank_card('6225xxxxxxxxxxxxxxx')
  Out[3]: '6225 xxxx xxxx xxxx xxx'
  ```

## References

[1] Brandon L Burnett@StackOverflow, [Split python string every nth character?](http://stackoverflow.com/questions/9475241/split-python-string-every-nth-character)

