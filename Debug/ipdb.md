# ipdb

## Installation

```shell
pip install ipdb
```

## Usage

```python
import ipdb; ipdb.set_trace()
```

## Commands

```
ipdb> h

Documented commands (type help <topic>):
========================================
EOF    bt         cont      enable  jump  pdef    psource  run      unt
a      c          continue  exit    l     pdoc    q        s        until
alias  cl         d         h       list  pfile   quit     step     up
args   clear      debug     help    n     pinfo   r        tbreak   w
b      commands   disable   ignore  next  pinfo2  restart  u        whatis
break  condition  down      j       p     pp      return   unalias  where

Miscellaneous help topics:
==========================
exec  pdb

Undocumented commands:
======================
retval  rv
```

* Commands Table

  | Command      | Description                              |
  | ------------ | ---------------------------------------- |
  | a(rgs)       | Print the argument list of the current function |
  | b(reak)      | With a filename:line number argument, set a break there. If filename is omitted, use the current file. With a function name, set a break at the first executable line of that function. Without argument, list all breaks. Each breakpoint is assigned a number to which all the other breakpoint commands refer |
  | c(ont(inue)) | Continue execution, only stop when a breakpoint is encountered |
  | cl(ear)      | With a space separated list of breakpoint numbers, clear those breakpoints. Without argument, clear all breaks (but first ask confirmation) |
  | d(own)       | Move the current frame one level down in the stack trace (to a newer frame) |
  | h(elp)       | Without argument, print the list of available commands. With a command name as argument, print help about that command (this is currently not implemented) |
  | j(ump)       | `j` jumps to the given line of code, actually skipping the execution of anything between |
  | l(ist)       | List source code for the current file. Without arguments, list 11 lines around the current line or continue the previous listing. With one argument, list 11 lines starting at that line. With two arguments, list the given range; if the second argument is less than the first, it is a count |
  | n(ext)       | Continue execution until the next line in the current function is reached or it returns |
  | p(rint)      | Print the value of the expression        |
  | q(uit)       | Quit from the debugger                   |
  | r(eturn)     | Continue execution until the current function returns |
  | run          | Restart the debugged python program. If a string is supplied it is splitted with "shlex", and the result is used as the new sys.argv. History, breakpoints, actions and debugger options are preserved. "restart" is an alias for "run" |
  | s(tep)       | Execute the current line, stop at the first possible occasion (either in a function that is called or in the current function) |
  | tbreak       | Temporary breakpoint, which is removed automatically when it is first hit. The arguments are the same as break |
  | unt(il)      | Continue execution until the line with a number greater than the current one is reached or until the current frame returns |
  | u(p)         | Move the current frame one level up in the stack trace (to an older frame) |
  | w(here)      | Print a stack trace, with the most recent frame at the bottom. An arrow indicates the "current frame", which determines the context of most commands |
  | ENTER        | repeat previous                          |

## References

[1] georgejhunt, [The IPdb debug commands](http://georgejhunt.com/olpc/pydebug/pydebug/ipdb.html)