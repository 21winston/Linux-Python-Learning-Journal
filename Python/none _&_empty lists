# Python Layout Mechanics

## Pre-allocation
Use `[None] * 10` to reserve slots. `[]` has no slots (index assignment crashes). `[0] * 10` works but avoid it if `0` is a real value in your data.

## Centering
```python
left_margin = (screen_width - box_width) // 2
```
Use `//` to avoid floats. No right margin needed — `print()` adds a newline automatically.

## Component Budgeting
Every character takes up space. If your box must be exactly `box_width` wide, subtract what you hardcode:
```python
'+' + '-' * (box_width - 2) + '+'  # corners take 2, middle gets the rest
```

## Alignment Rule
Every row in a frame must add up to the same total width or the walls go crooked. If borders are `|  ` and `  |` (3 chars each), your content + padding must fill the remaining `box_width - 6` characters.

## `print()`
`print()` with no arguments outputs a blank line in the terminal. It controls visual spacing in your program's output — nothing to do with blank lines in your code.
