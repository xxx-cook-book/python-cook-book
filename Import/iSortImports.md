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
  # See the menu of settings available here:
  #   https://github.com/timothycrosley/isort/wiki/isort-Settings

  [settings]
  indent='    '
  line_length=200
  lines_after_imports=2
  skip=migrations
  ```

  * [isort Settings](https://github.com/timothycrosley/isort/wiki/isort-Settings)

* isort.sh

  * Before isort==4.2.5

    ```shell
    #!/bin/bash

    isort -rc .  # work
    isort -rc -sp . .  # work
    isort -rc -sp .isort.cfg .  # not work
    isort -rc -sp ./.isort.cfg .  # work
    ```

  * If you really want to use command ``isort -rc -sp .isort.cfg .``

    * https://github.com/timothycrosley/isort/pull/429/

* exec

  ```shell
  ./isort.sh
  ```

## References

[1] isort@TT4IT, [isort — A Python utility / library to sort imports.](http://tt4it.com/resources/discuss/2302/)

