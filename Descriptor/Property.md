# Property

*New In Python 2.2*

*Changed In Python 2.6: The `getter`, `setter`, and `deleter` attributes were added.*

```
property(fget=None, fset=None, fdel=None, doc=None) -> property attribute
```

## Usage

```python
import datetime

class Student(object):
    
    birth_year = 1988
    
    def get_birth_year(self):
        return self.birth_year
    
    def set_birth_year(self, value):
        self.birth_year = value
    
    birth_year = property(get_birth_year, set_birth_year)
    
    def get_age(self):
        return datetime.date.today().year - self.birth_year
    
    age = property(get_age)
```

Since Python 2.6

```python
import datetime

class Student(object):

    birth_year = 1988

    @property
    def birth_year(self):
        return self.birth_year
    
    @birth_year.setter
    def birth_year(self, value):
        self.birth_year = value
    
    @property
    def age(self):
        return datetime.date.today().year - self.birth_year
```

Property parameter not support

```python
@property
def age(self, birth_year):
    xxx
```

## References

[1] Docs@Python, [2. Built-in Functions — property](https://docs.python.org/2/library/functions.html#property)