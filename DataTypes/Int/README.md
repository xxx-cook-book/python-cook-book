# Int

## base
```
int(x=0) -> int or long
int(x, base=10) -> int or long

Base 0 means to interpret the base from the string as an integer literal.
>>> int('0b100', base=0)
4
```
* Examples
  ```
  In [7]: int('0x01')
  ---------------------------------------------------------------------------
  ValueError                                Traceback (most recent call last)
  <ipython-input-7-7ce568972738> in <module>()
  ----> 1 int('0x01')
    
  ValueError: invalid literal for int() with base 10: '0x01'
    
  In [8]: int('0x01', 16)
  Out[8]: 1
    
  In [9]: int('0x01', 0)
  Out[9]: 1
  ```