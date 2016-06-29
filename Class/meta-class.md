# MetaClass

## type

``class Hello(object)`` <==> ``type('Hello', (object, ), dict())``

* class

  ```python
  class Hello(object):
      def __init__(self):
          pass
  ```

* type

  ```python
  def _init__(self):
      pass

  type('Hello', (object, ), dict(__init__=__init__))
  ```


* See [django-excel-response2/blob/master/excel_response2.py](https://github.com/Brightcells/django-excel-response2/blob/master/excel_response2.py#L107)

## metaclass

* See [Simple ORM using metaclass](https://github.com/michaelliao/learn-python/blob/master/metaclass/simple_orm.py)

## References

[1] Ivan Smirnov's Blog, [Python metaclasses](http://ivansmirnov.io/python-metaclasses/)