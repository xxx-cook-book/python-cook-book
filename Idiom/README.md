# Idiom

## ``LBYL`` vs. ``EAFP``

* LBYL

  Look Before You Leap
  ```python
  if os.path.exists(filename):
      os.remove(filename)
  ```

* EAFP

  Easier to Ask Forgiveness than to get Permission
  ```python
  try:
      os.remove(filename)
  except OSError as e:
      if e.errno != errno.ENOENT:
          raise
  ```

## References

