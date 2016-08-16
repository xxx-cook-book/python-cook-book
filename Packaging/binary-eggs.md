# Binary Eggs

## Lost Source Codes

* Trees

  ```shell
  $ tree django_rlog
  django_rlog
  ├── __init__.py
  └── management
      ├── __init__.py
      └── commands
          ├── __init__.py
          ├── rlog.py
          └── rstop.py

  2 directories, 7 files
  ```


* Setup.py

  ```python
  # -*- coding: utf-8 -*-

  from setuptools import setup

  version = '1.0.3'

  setup(
      name='django-rlog',
      version=version,
      keywords='django-rlog',
      description='Save rlog\'s Pub/Sub Log to Disk',
      long_description=open('README.rst').read(),
    
      url='https://github.com/django-xxx/django-rlog',
    
      author='Hackathon',
      author_email='kimi.huang@brightcells.com',
    
      packages=['django_rlog'],
      py_modules=[],
      install_requires=['django-six'],
      include_package_data=True,
    
      classifiers=[
          'Development Status :: 5 - Production/Stable',
          'Environment :: Web Environment',
          'Framework :: Django',
          'Intended Audience :: Developers',
          'Programming Language :: Python',
          'Topic :: Software Development :: Libraries :: Python Modules',
          'Topic :: Office/Business :: Financial :: Spreadsheet',
      ],
  )
  ```

* ``management/__init__.py``

  * Empty

    ``python setup.py install`` just have ``.egg``，not have source codes.

  * Some Codes

    ```python
    # -*- coding: utf-8 -*-

    import os

    os.path.abspath(__file__)
    ```
    ​ ``python setup.py install`` have ``.egg``，also have source codes.


* See [django-xxx/django-logit](https://github.com/django-xxx/django-logit)

## References