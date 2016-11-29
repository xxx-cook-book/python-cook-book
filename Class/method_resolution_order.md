# Method Resolution Order(MRO)

## Classes

* *Classic classes*

  *Before Python 2.2*

  *Can not use super*

  ```python
  In [1]: class A():
     ...:     def __init__(self):
     ...:         self.a = 1
     ...:         

  In [2]: class B():
     ...:     def __init__(self):
     ...:         self.b = 2
     ...: 

  In [3]: class C(A, B):
     ...:     def __init__(self):
     ...:         super(C, self).__init__()
     ...:         

  In [4]: c = C()
  ---------------------------------------------------------------------------
  TypeError                                 Traceback (most recent call last)
  <ipython-input-4-607856e02023> in <module>()
  ----> 1 c = C()

  <ipython-input-3-fca959ece800> in __init__(self)
        1 class C(A, B):
        2     def __init__(self):
  ----> 3         super(C, self).__init__()
        4 

  TypeError: super() argument 1 must be type, not classobj
  ```

* *New style classes*

  *Since Python 2.2*

  ```python
  # Classic classes
  class A():
      pass

  # New style classes
  class A(object):
      pass
  ```

## MRO

* *Old method resolution order*

  *Before Python 2.3*

  ```
  depth first and then left to right
  ```

* *C3 method resolution order*

  *Since Python 2.3*

  *Can call ``instance.__mro__`` & ``instance.mro()``*

  ```python
  In [1]: class A(object):
     ...:     def __init__(self):
     ...:         self.a = 1
     ...:         

  In [2]: class B(object):
     ...:     def __init__(self):
     ...:         self.b = 2
     ...:         

  In [3]: class C(A, B):
     ...:     pass
     ...: 

  In [4]: C.__mro__
  Out[4]: (__main__.C, __main__.A, __main__.B, object)

  In [5]: C.mro()
  Out[5]: [__main__.C, __main__.A, __main__.B, object]
  ```

## Multiple-inheritance

* *Classic classes*

  * *Parent Not Super* & *Child Not Super*

    ```python
    In [1]: class A():
       ...:     def __init__(self):
       ...:         self.a = 1
       ...:         

    In [2]: class B():
       ...:     def __init__(self):
       ...:         self.b = 2
       ...:         

    In [3]: class C(A, B):
       ...:     pass
       ...: 

    In [4]: c = C()

    In [5]: c.a
    Out[5]: 1

    In [6]: c.b
    ---------------------------------------------------------------------------
    AttributeError                            Traceback (most recent call last)
    <ipython-input-6-6be2854bea30> in <module>()
    ----> 1 c.b

    AttributeError: C instance has no attribute 'b'
    ```

  * *Parent Not Super* & *Child Not Super*

    ```python
    In [1]: class A():
       ...:     def __init__(self):
       ...:         self.a = 1
       ...:         

    In [2]: class B():
       ...:     def __init__(self):
       ...:         self.b = 2
       ...:         

     In [3]: class C(A, B):
       ...:     def __init__(self):
       ...:         A.__init__(self)
       ...:         B.__init__(self)
       ...:

    In [4]: c = C()

    In [5]: c.a
    Out[5]: 1

    In [6]: c.b
    Out[6]: 2
    ```

* *New style classes*

  * *Parent Not Super*

    ```python
    In [1]: class A(object):
       ...:     def __init__(self):
       ...:         self.a = 1
       ...:         

    In [2]: class B(object):
       ...:     def __init__(self):
       ...:         self.b = 2
       ...:         

    In [3]: class C(A, B):
       ...:     pass
       ...: 
    # In [3]: class C(A, B):
    #   ...:     def __init__(self):
    #   ...:         super(C, self).__init__()
    #   ...:

    In [4]: c = C()

    In [5]: c.a
    Out[5]: 1

    In [6]: c.b
    ---------------------------------------------------------------------------
    AttributeError                            Traceback (most recent call last)
    <ipython-input-6-6be2854bea30> in <module>()
    ----> 1 c.b

    AttributeError: 'C' object has no attribute 'b'
    ```

  * *One Parent Super*

    ```python
    In [1]: class A(object):
       ...:     def __init__(self):
       ...:         self.a = 1
       ...:         super(A, self).__init__()
       ...:         

    In [2]: class B(object):
       ...:     def __init__(self):
       ...:         self.b = 2
       ...:         

    In [3]: class C(A, B):
       ...:     def __init__(self):
       ...:         super(C, self).__init__()
       ...:         

    In [4]: c = C()

    In [5]: c.a
    Out[5]: 1

    In [6]: c.b
    Out[6]: 2

    In [7]: class D(B, A):
       ....:     def __init__(self):
       ....:         super(D, self).__init__()
       ....:         

    In [8]: d = D()

    In [9]: d.a
    ---------------------------------------------------------------------------
    AttributeError                            Traceback (most recent call last)
    <ipython-input-12-769f1638fd85> in <module>()
    ----> 1 d.a

    AttributeError: 'D' object has no attribute 'a'

    In [10]: d.b
    Out[10]: 2
    ```


## Order

```python
class A(object):  
    def __init__(self):  
        super(A, self).__init__()  
        print "A!"  
  
class B(object):  
    def __init__(self):  
        super(B, self).__init__()  
        print "B!"  
  
class AB(A, B):  
    def __init__(self):  
        super(AB, self).__init__()  
        print "AB!"  
  
class C(object):  
    def __init__(self):  
        super(C,  self).__init__()  
        print "C!"  
  
class D(object):  
    def __init__(self):  
        super(D, self).__init__()  
        print "D!"  
  
class CD(C, D):  
    def __init__(self):  
        super(CD, self).__init__()  
        print "CD!"  
  
class ABCD(AB, CD):  
    def __init__(self):  
        super(ABCD, self).__init__()  
        print "ABCD!"  
  
ABCD()

# D!
# C!
# CD!
# B!
# A!
# AB!
# ABCD!
```

## References

[1] Docs@Python, [9. Classes - 9.5.1. Multiple Inheritance](https://docs.python.org/3/tutorial/classes.html#multiple-inheritance)

[2] Releases@Python, [The Python 2.3 Method Resolution Order](https://www.python.org/download/releases/2.3/mro/)

[3] zjm1126@StackOverflow, [What does “mro()” do in Python?](http://stackoverflow.com/questions/2010692/what-does-mro-do-in-python)