# Style Guide

* [iSort — A Python utility / library to sort imports](../Import/iSortImports.md)

* [PEP 8 — Style Guide for Python Code](PEP8.md)

* check — Script to exec isort and pep8 

  * check.sh

    ```shell
    #!/bin/bash

    echo '>> iSort'
    ./isort.sh
    echo

    echo '>> PEP8'
    ./pep8.sh
    echo
    ```
  * exec
    ```shell
    ./check.sh
    ```


