# Strftime
## Directive

Python's `strftime` directives

Examples are based on `datetime.datetime(2013, 9, 30, 7, 6, 5)`

* The following is a list of all the format codes that the C standard (1989 version) requires, and these work on all platforms with a standard C implementation. Note that the 1999 version of the C standard added additional format codes.

  | Directive | Meaning                                  | Example                    |
  | --------- | ---------------------------------------- | -------------------------- |
  | `%a`      | Weekday as locale’s abbreviated name.    | `Mon`                      |
  | `%A`      | Weekday as locale’s full name.           | `Monday`                   |
  | `%w`      | Weekday as a decimal number, where 0 is Sunday and 6 is Saturday. | `1`                        |
  | `%d`      | Day of the month as a zero-padded decimal number. | `30`                       |
  | `%-d`     | Day of the month as a decimal number. (Platform specific) | `30`                       |
  | `%b`      | Month as locale’s abbreviated name.      | `Sep`                      |
  | `%B`      | Month as locale’s full name.             | `September`                |
  | `%m`      | Month as a zero-padded decimal number.   | `09`                       |
  | `%-m`     | Month as a decimal number. (Platform specific) | `9`                        |
  | `%y`      | Year without century as a zero-padded decimal number. | `13`                       |
  | `%Y`      | Year with century as a decimal number.   | `2013`                     |
  | `%H`      | Hour (24-hour clock) as a zero-padded decimal number. | `07`                       |
  | `%-H`     | Hour (24-hour clock) as a decimal number. (Platform specific) | `7`                        |
  | `%I`      | Hour (12-hour clock) as a zero-padded decimal number. | `07`                       |
  | `%-I`     | Hour (12-hour clock) as a decimal number. (Platform specific) | `7`                        |
  | `%p`      | Locale’s equivalent of either AM or PM.  | `AM`                       |
  | `%M`      | Minute as a zero-padded decimal number.  | `06`                       |
  | `%-M`     | Minute as a decimal number. (Platform specific) | `6`                        |
  | `%S`      | Second as a zero-padded decimal number.  | `05`                       |
  | `%-S`     | Second as a decimal number. (Platform specific) | `5`                        |
  | `%f`      | Microsecond as a decimal number, zero-padded on the left. | `000000`                   |
  | `%z`      | UTC offset in the form +HHMM or -HHMM (empty string if the the object is naive). | ``                         |
  | `%Z`      | Time zone name (empty string if the object is naive). | ``                         |
  | `%j`      | Day of the year as a zero-padded decimal number. | `273`                      |
  | `%-j`     | Day of the year as a decimal number. (Platform specific) | `273`                      |
  | `%U`      | Week number of the year (Sunday as the first day of the week) as a zero padded decimal number. All days in a new year preceding the first Sunday are considered to be in week 0. | `39`                       |
  | `%W`      | Week number of the year (Monday as the first day of the week) as a decimal number. All days in a new year preceding the first Monday are considered to be in week 0. | `39`                       |
  | `%c`      | Locale’s appropriate date and time representation. | `Mon Sep 30 07:06:05 2013` |
  | `%x`      | Locale’s appropriate date representation. | `09/30/13`                 |
  | `%X`      | Locale’s appropriate time representation. | `07:06:05`                 |
  | `%%`      | A literal '%' character.                 | `%`                        |

* Several additional directives not required by the C89 standard are included for convenience. These parameters all correspond to ISO 8601 date values. These may not be available on all platforms when used with the [:meth:`strftime`](https://github.com/python/cpython/blob/6ebe774473c5db2365f618e50c3f0769fa87a537/Doc/library/datetime.rst#id384)method. The ISO 8601 year and ISO 8601 week directives are not interchangeable with the year and week number directives above. Calling [:meth:`strptime`](https://github.com/python/cpython/blob/6ebe774473c5db2365f618e50c3f0769fa87a537/Doc/library/datetime.rst#id386) with incomplete or ambiguous ISO 8601 directives will raise a [:exc:`ValueError`](https://github.com/python/cpython/blob/6ebe774473c5db2365f618e50c3f0769fa87a537/Doc/library/datetime.rst#id388).

  | Directive | Meaning                                  | Example |
  | --------- | ---------------------------------------- | ------- |
  | `%G`      | ISO 8601 year with century representing the year that contains the greater part of the ISO week (%V). | `2013`  |
  | `%u`      | ISO 8601 weekday as a decimal number where 1 is Monday. | `1`     |
  | `%V`      | The ISO 8601 week number of the current year (01 to 53), where week 1 is the first week that has at least 4 days in the current year, and with Monday as the first day of the week. | `40`    |

## Usage

* ``%Y-%m-%d %H:%M:%S``
  * Year-Month-Day Hour:Minute:Second
  * 2013-09-30 07:06:05

* ``%U`` vs ``%W``

  ```python
  In [86]: aaa = tc.string_to_local_datetime('2015-12-27 01:01:01')

  In [87]: tc.datetime_to_string(aaa, format='%U')
  Out[87]: '52'

  In [88]: tc.datetime_to_string(aaa, format='%W')
  Out[88]: '51'
  ```

* Week

  ```python
  In [48]: lastday = tc.string_to_local_datetime('2015-12-31 01:01:01')

  In [49]: lastday
  Out[49]: datetime.datetime(2015, 12, 31, 1, 1, 1)

  In [50]: tc.datetime_to_string(lastday, format='%W')
  Out[50]: '52'

  In [51]: firstday = tc.string_to_local_datetime('2016-01-01 01:01:01')

  In [52]: firstday
  Out[52]: datetime.datetime(2016, 1, 1, 1, 1, 1)

  In [53]: tc.datetime_to_string(firstday, format='%W')
  Out[53]: '00'
      
  In [54]: tc.datetime_to_string(firstday, format='%V')
  Out[54]: '53'
  ```

## References

[1] mccutchen@Github, [A single-serving-site that provides a reference for Python's strftime formatting options](https://github.com/mccutchen/strftime.org)

[2] Docs@Python, [8.1. datetime — Basic date and time types ==> 8.1.7. strftime() and strptime() Behavior](https://docs.python.org/2/library/datetime.html#strftime-and-strptime-behavior)

[3] cpython@Github, [Issue #26678: Merge datetime doc fixes from 3.5](https://github.com/python/cpython/blob/6ebe774473c5db2365f618e50c3f0769fa87a537/Doc/library/datetime.rst)

[4] TutorialsPoint, [Python time strftime() Method](http://www.tutorialspoint.com/python/time_strftime.htm)
