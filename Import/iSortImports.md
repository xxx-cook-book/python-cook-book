# iSort Imports

## iSort

A Python utility / library to sort imports

## Installation

```shell
pip install isort
```

## Usage

* Appointed

  ```shell
  isort mypythonfile.py mypythonfile2.py
  ```

* ALL

  ```
  isort -rc .
  ```

  * Equivalent to ``isort **/*.py``


## Configuration

* .isort.cfg

  ```
  [settings]
  indent='    '
  line_length=120
  skip=migrations
  ```

  * [isort Settings](https://github.com/timothycrosley/isort/wiki/isort-Settings)

* isort.sh

  ```shell
  #!/bin/bash

  isort -rc --settings-path .isort.cfg .
  ```


* exec

  ```shell
  ./isort.sh
  ```

## References

[1] isort@TT4IT, [isort — A Python utility / library to sort imports.](http://tt4it.com/resources/discuss/2302/)

