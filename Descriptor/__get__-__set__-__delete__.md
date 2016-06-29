# ``__get__``/``__set__``/``__delete__``

## [Descriptor Protocol](https://docs.python.org/2/howto/descriptor.html#id4)

`descr.__get__(self, obj, type=None) --> value`

`descr.__set__(self, obj, value) --> None`

`descr.__delete__(self, obj) --> None`

That is all there is to it. Define any of these methods and an object is considered a descriptor and can override default behavior upon being looked up as an attribute.

If an object defines both [`__get__()`](https://docs.python.org/2/reference/datamodel.html#object.__get__) and [`__set__()`](https://docs.python.org/2/reference/datamodel.html#object.__set__), it is considered a data descriptor. Descriptors that only define [`__get__()`](https://docs.python.org/2/reference/datamodel.html#object.__get__) are called non-data descriptors (they are typically used for methods but other uses are possible).

Data and non-data descriptors differ in how overrides are calculated with respect to entries in an instance’s dictionary. If an instance’s dictionary has an entry with the same name as a data descriptor, the data descriptor takes precedence. If an instance’s dictionary has an entry with the same name as a non-data descriptor, the dictionary entry takes precedence.

To make a read-only data descriptor, define both [`__get__()`](https://docs.python.org/2/reference/datamodel.html#object.__get__) and [`__set__()`](https://docs.python.org/2/reference/datamodel.html#object.__set__) with the [`__set__()`](https://docs.python.org/2/reference/datamodel.html#object.__set__) raising an [`AttributeError`](https://docs.python.org/2/library/exceptions.html#exceptions.AttributeError) when called. Defining the [`__set__()`](https://docs.python.org/2/reference/datamodel.html#object.__set__) method with an exception raising placeholder is enough to make it a data descriptor.

