# Software Version Comparison

## versions

Python library for software version comparison

## Installation

```shell
pip install versions
```

## Usage

* Compare versions

  ```python
  >>> from versions import Version
  >>> Version.parse('2.0.0') > Version.parse('1.0.0')
  True
  ```

* Test if constraints are satisfied by a version

  ```python
  >>> from versions import Constraint, Constraints
  >>> '2.0' in Constraint.parse('>1')
  True
  >>> '1.5' in Constraints.parse('>1,<2')
  True
  ```


* InvalidVersionExpression

  ```python
  from versions import Version
  from versions.version import InvalidVersionExpression

  try:
      Version.parse('a.b.c')
  except InvalidVersionExpression:
      # do something
      pass
  ```

## References

[1] versions@TT4IT, [versions — Python library for software version comparison](http://tt4it.com/resources/discuss/2221/)

