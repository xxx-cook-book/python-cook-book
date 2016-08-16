# Delete File or Dir

``os.remove()`` will remove a file.

``os.rmdir()`` will remove an empty directory.

``shutil.rmtree()`` will delete a directory and all its contents.

## os.remove

```python
In [1]: os.remove('/tmp/debug.log')

In [2]: os.remove('/tmp/debug.log')
---------------------------------------------------------------------------
FileNotFoundError                         Traceback (most recent call last)
<ipython-input-3-870588b0988b> in <module>()
----> 1 os.remove('/tmp/debug.log')

FileNotFoundError: [Errno 2] No such file or directory: '/tmp/debug.log'
        
In [3]: try:
   ...:     os.remove('/tmp/debug.log')
   ...: except OSError:
   ...:     pass
   ...:

In [4]: try:
   ...:     os.remove('/tmp/debug.log')
   ...: except OSError as e:
   ...:     if e.errno != errno.ENOENT:
   ...:         raise
   ...:
```

* ``OSError`` vs. ``FileNotFoundError``
  * In 3.3, [`IOError` became an alias for `OSError`](http://docs.python.org/3.3/library/exceptions.html#IOError), and `FileNotFoundError` is a subclass of `OSError`.

## References

[1] Scott Wilson@StackOverflow, [Most pythonic way to delete a file which may not exist](http://stackoverflow.com/questions/10840533/most-pythonic-way-to-delete-a-file-which-may-not-exist)

[2] PEPS@Python Developer's Guide, [PEP 3151 -- Reworking the OS and IO exception hierarchy](https://www.python.org/dev/peps/pep-3151/#lack-of-fine-grained-exceptions)