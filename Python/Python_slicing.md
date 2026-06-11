# TIL: Python Slicing and Module Shadowing

A few things I learned while working through *Beginning Python (4th Edition)*.

## Slicing with a Step

Given:

```python
numbers = [1,2,3,4,5,6,7,8,9,10]
```

The slice:

```python
numbers[3:6:3]
```

returns:

```python
[4]
```

Why?

* Start at index `3` → value `4`
* Move forward by `3` positions → next index would be `6`
* The stop index is exclusive, so index `6` is not included

Only `4` is collected.

## Slice Syntax

Slice notation only works on an existing sequence.

Incorrect:

```python
numbers = [3:6:3]
```

This raises a `SyntaxError`.

Correct:

```python
numbers[3:6:3]
```

## Module Shadowing

Avoid naming your scripts after Python standard library modules.

For example:

```text
calendar.py
json.py
string.py
```

can cause import conflicts because Python may load your file instead of the built-in module.

A safer naming style is:

```text
calendar_practice.py
json_exercises.py
string_notes.py
```

## Takeaway

When debugging, check three things first:

1. Is the syntax valid?
2. Am I slicing the sequence I think I am?
3. Did I accidentally name a file after a built-in Python module?
