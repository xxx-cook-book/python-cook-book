# Python/C API

## C Codes

* demo.c

  ```c
  int add(int x, int y){
      return x + y;
  }

  //int main(void){
  //    printf("%d", add(1, 2));
  //    return 0;
  //}

  #include<Python.h>

  static PyObject* W_add(PyObject* self, PyObject* args){
      int x;
      int y;
      if(!PyArg_ParseTuple(args, "i|i", &x, &y)){
          return NULL;
      } else {
          return Py_BuildValue("i", add(x, y));
      }
  }

  static PyMethodDef ExtendMethods[] = {
      {"add", W_add, METH_VARARGS, "a function from C"},
      {NULL, NULL, 0, NULL},
  };

  //initxxx, xxx should be this file name
  //if spam.c => spam.so
  //when import spam will raise ImportError
  //ImportError: dynamic module does not define init function (initspam)
  //-o xxx.so, xxx also should be this file name
  PyMODINIT_FUNC initdemo(){
      Py_InitModule("demo", ExtendMethods);
  }
  ```

* Compilation and Linkage

  * Command
    ```shell
    gcc demo.c -I /usr/include/python2.6 -shared -o demo.so
    ```

    *  ``Ubuntu 12.04.5 LTS`` raise error

       ```shell
       $ gcc demo.c -I /usr/include/python2.7 -shared -o demo.so
       /usr/bin/ld: /tmp/cceeXldr.o: relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
       /tmp/cceeXldr.o: could not read symbols: Bad value
       collect2: ld returned 1 exit status
       ```
       *  Recompile with ``-fPIC`` works

          ```shell
          gcc demo.c -I /usr/include/python2.6 -shared -fPIC -o demo.so
          ```

    *  ``Mac OS X`` raise error

       ```shell
        $ gcc demo.c -I /usr/include/python2.7 -shared -o demo.so
        Undefined symbols for architecture x86_64:
          "_PyArg_ParseTuple", referenced from:
              _W_add in demo-00439c.o
          "_Py_BuildValue", referenced from:
              _W_add in demo-00439c.o
          "_Py_InitModule4_64", referenced from:
              _initdemo in demo-00439c.o
        ld: symbol(s) not found for architecture x86_64
        clang: error: linker command failed with exit code 1 (use -v to see invocation)
       ```

* Tips
  * if note off main function

    ```shell
    $ gcc demo.c -I /usr/include/python2.7 -shared -fPIC -o demo.so
    demo.c: In function ‘main’:
    demo.c:6:5: warning: incompatible implicit declaration of built-in function ‘printf’ [enabled by default]
    ```

  * and not note off printf works

    ```c
    int main(void){
    //    printf("%d", add(1, 2));
        return 0;
    }
    ```

## Python Building Extension

* Setup.py
  * https://github.com/urwid/urwid/blob/master/setup.py

    ```shell
    building 'urwid.str_util' extension
    creating build/temp.macosx-10.9-intel-2.7
    creating build/temp.macosx-10.9-intel-2.7/source
    cc -fno-strict-aliasing -fno-common -dynamic -arch x86_64 -arch i386 -g -Os -pipe -fno-common -fno-strict-aliasing -fwrapv -DENABLE_DTRACE -DMACOSX -DNDEBUG -Wall -Wstrict-prototypes -Wshorten-64-to-32 -DNDEBUG -g -fwrapv -Os -Wall -Wstrict-prototypes -DENABLE_DTRACE -arch x86_64 -arch i386 -pipe -I/System/Library/Frameworks/Python.framework/Versions/2.7/include/python2.7 -c source/str_util.c -o build/temp.macosx-10.9-intel-2.7/source/str_util.o
    cc -bundle -undefined dynamic_lookup -arch x86_64 -arch i386 -Wl,-F. build/temp.macosx-10.9-intel-2.7/source/str_util.o -o build/lib.macosx-10.9-intel-2.7/urwid/str_util.so
    ```

## References

[1] Docs@Python, [Extending Python with C or C++](https://docs.python.org/2/extending/extending.html)

[2] Docs@Python, [Python/C API Reference Manual](https://docs.python.org/2/c-api/index.html)

[3] O'Reilly's CD bookshelf, [24.1 Extending Python with Python's C API](http://docstore.mik.ua/orelly/other/python/0596001886_pythonian-chp-24-sect-1.html)

[4] user1667191@StackOverflow, [Compilation fails with “relocation R_X86_64_32 against `.rodata.str1.8' can not be used when making a shared object”](http://stackoverflow.com/questions/19364969/compilation-fails-with-relocation-r-x86-64-32-against-rodata-str1-8-can-not)