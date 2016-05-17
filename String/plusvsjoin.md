# + vs join

String join is significantly faster then concatenation.

Why? Strings are immutable and can't be changed in place. To alter one, a new representation needs to be created (a concatenation of the two)

## References

[1] Wayne Werner@StackOverflow, [How slow is Python's string concatenation vs. str.join?](http://stackoverflow.com/questions/3055477/how-slow-is-pythons-string-concatenation-vs-str-join)

[2] Blog@waymoot, [Efficient String Concatenation in Python](https://waymoot.org/home/python_string/)