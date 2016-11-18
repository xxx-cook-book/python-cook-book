# Requirement.txt

## Create

```shell
pip freeze | sort > requirement.txt  # alias sort='LC_ALL=C sort'
pip freeze | LC_ALL=C sort > requirement.txt
```

## Install

```shell
pip install -r requirements.txt
```

## References
