## 📅 Featured Script: Date Formatter 

This project is based on an exercise from Chapter 2 of *Beginning Python* by Magnus Lie Hetland. It demonstrates how Python lists, indexing, user input, and string manipulation can be used to convert numerical date values into a human-readable format.

### Concepts Practiced

* Python lists
* Sequence indexing
* User input with `input()`
* Integer conversion using `int()`
* String concatenation
* Executable Python scripts using shebangs

### Changes from the Book Example

* Reformatted the output from `April 5th, 2014` to `5th April, 2014`
* Added a shebang (`#!/usr/bin/env python3`) to support direct execution on Unix-like systems

### Source Code

```python
#!/usr/bin/env python3

months = [
    'January', 'February', 'March', 'April',
    'May', 'June', 'July', 'August',
    'September', 'October', 'November', 'December'
]

endings = (
    ['st', 'nd', 'rd']
    + 17 * ['th']
    + ['st', 'nd', 'rd']
    + 7 * ['th']
    + ['st']
)

year = input('Year: ')
month = input('Month (1-12): ')
day = input('Day (1-31): ')

month_number = int(month)
day_number = int(day)

month_name = months[month_number - 1]
ordinal = day + endings[day_number - 1]

print(ordinal + ' ' + month_name + ', ' + year)
```

### Example

```text
Year: 2014
Month (1-12): 4
Day (1-31): 5

5th April, 2014
```
