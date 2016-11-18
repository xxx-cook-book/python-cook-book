# Upload PyPI

## setup.py

## twine

1. Create some distributions in the normal way:

   ```
   $ python setup.py sdist bdist_wheel
   ```

2. Upload with twine:

   ```
   $ twine upload dist/*
   ```

3. Done!

## References

[1] Docs@Packaging, [Packaging and Distributing Projects](https://packaging.python.org/distributing/)