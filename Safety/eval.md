# eval

## eval

* eval is evil
* use ast.literal_eval instead

## literal_eval

Safely evaluate an expression node or a Unicode or *Latin-1* encoded string containing a Python literal or container display. The string or node provided may only consist of the following Python literal structures: strings, numbers, tuples, lists, dicts, booleans, and `None`.

This can be used for safely evaluating strings containing Python values from untrusted sources without the need to parse the values oneself. It is not capable of evaluating arbitrarily complex expressions, for example involving operators or indexing.

## References

[1] Library@Python, [32.2. ast — Abstract Syntax Trees — ast.literal_eval(node_or_string)](https://docs.python.org/2/library/ast.html#ast.literal_eval)