# MetaClass

## type

``class Hello(object)`` <==> ``type('Hello', (object, ), dict())``

* class

  ```python
  class Hello(object):
      def __init__(self):
          self.meta = 110
          print self.foo
          print self.bar()
      
      @property
      def foo(self):
          return self.meta
      
      def bar(self, plus=1):
          return self.meta + 1
      
  hello = Hello()
  # 110
  # 111
  ```

* type

  ```python
  def __init__(self):
      self.meta = 110
      print self.foo
      print self.bar()
      
  @property
  def foo(self):
      return self.meta

  def bar(self, plus=1):
      return self.meta + 1

  Hello = type('Hello', (object, ), dict(__init__=__init__, foo=foo, bar=bar))

  hello = Hello()
  # 110
  # 111
  ```


* See [django-excel-response2/blob/master/excel_response2.py](https://github.com/Brightcells/django-excel-response2/blob/master/excel_response2.py#L107)

## metaclass

* See [Simple ORM using metaclass](https://github.com/michaelliao/learn-python/blob/master/metaclass/simple_orm.py)

## References

[1] Ivan Smirnov's Blog, [Python metaclasses](http://ivansmirnov.io/python-metaclasses/)