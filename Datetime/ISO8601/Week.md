# Week
## Python

* .isocalendar()

  ```python
  In [114]: from TimeConvert import TimeConvert as tc
      
  In [115]: oneday = tc.string_to_local_datetime('2015-12-28 01:01:01')

  In [116]: oneday
  Out[116]: datetime.datetime(2015, 12, 28, 1, 1, 1)

  In [117]: oneday.isocalendar()[1]
  Out[117]: 53

  In [118]: oneday.date().isocalendar()[1]
  Out[118]: 53
  ```

* isoweek

  * Installation

    ```shell
    pip install isoweek
    ```

  * Usage

    ```python
    In [137]: from isoweek import Week

    In [138]: w = Week.thisweek()
        
    In [139]: w
    Out[139]: isoweek.Week(2016, 18)

    In [140]: lw = w - 18

    In [141]: lw
    Out[141]: isoweek.Week(2015, 53)
        
    In [142]: lw.days()
    Out[142]:
    [datetime.date(2015, 12, 28),
     datetime.date(2015, 12, 29),
     datetime.date(2015, 12, 30),
     datetime.date(2015, 12, 31),
     datetime.date(2016, 1, 1),
     datetime.date(2016, 1, 2),
     datetime.date(2016, 1, 3)]

    In [143]: lw.monday()
    Out[143]: datetime.date(2015, 12, 28)
    ```

* .strftime('%v')

  ```python
  In [150]: from TimeConvert import TimeConvert as tc
      
  In [151]: oneday = tc.string_to_local_datetime('2016-01-01 01:01:01')

  In [152]: tc.datetime_to_string(oneday, format='%V')
  Out[152]: '53'
  ```

## Java

```java
/* Build a calendar suitable to extract ISO8601 week numbers
 * (see http://en.wikipedia.org/wiki/ISO_8601_week_number) */
Calendar calendar = Calendar.getInstance();
calendar.setMinimalDaysInFirstWeek(4);
calendar.setFirstDayOfWeek(Calendar.MONDAY);

/* Set date */
calendar.setTime(date);

/* Get ISO8601 week number */
calendar.get(Calendar.WEEK_OF_YEAR);
```

* [What is a good, simple way to compute ISO 8601 week number?](http://stackoverflow.com/questions/147178/what-is-a-good-simple-way-to-compute-iso-8601-week-number)

## Android

```java
public int getWeekNumber ()

Added in API level 3
Computes the week number according to ISO 8601. The current Time object must already be normalized because this method uses the yearDay and weekDay fields.

In IS0 8601, weeks start on Monday. The first week of the year (week 1) is defined by ISO 8601 as the first week with four or more of its days in the starting year. Or equivalently, the week containing January 4. Or equivalently, the week with the year's first Thursday in it.

The week number can be calculated by counting Thursdays. Week N contains the Nth Thursday of the year.

Returns
int	the ISO week number.
```

* [android/text/format/Time](http://developer.android.com/reference/android/text/format/Time.html)
* [AndroidSDKSources/android-sdk-sources-for-api-level-3](https://github.com/AndroidSDKSources/android-sdk-sources-for-api-level-3/blob/caf0e61c078e35b8c65ab1c2994a6dd5541e8b1a/android/text/format/Time.java)

## Objective-C

```objective-c
NSCalendar *calendar = [[NSCalendar alloc] initWithCalendarIdentifier:NSCalendarIdentifierISO8601];
NSUInteger components = kCFCalendarUnitWeekOfYear | kCFCalendarUnitYearForWeekOfYear;
NSDate *date = [NSDate date];
NSDateComponents *dateComponents = [calendar components:components fromDate:date];
NSLog(@"date: %@", date);
NSLog(@"yearForWeekOfYear: %ld", dateComponents.yearForWeekOfYear);
NSLog(@"weekday: %ld", dateComponents.weekday);
```

## References

[1] Gerry@StackOverflow, [How to get week number in Python?](http://stackoverflow.com/questions/2600775/how-to-get-week-number-in-python)