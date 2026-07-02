# Lists: `len`/`min`/`max` & Basic Operations

## `len`, `min`, `max`

```python
numbers = [100, 34, 678]
len(numbers)      # 3   -> number of elements
max(numbers)      # 678 -> largest element
min(numbers)      # 34  -> smallest element

max(2, 3)          # 3 -> args can be passed directly, not just a sequence
min(9, 3, 2, 5)    # 2
```

## Lists are Mutable
Unlike strings/tuples, lists can be changed in place.

### `list()` — convert sequence to list
```python
list('Hello')   # ['H', 'e', 'l', 'l', 'o']
```
Works on any sequence, not just strings.

### Item Assignment
```python
x = [1, 1, 1]
x[1] = 2        # x -> [1, 2, 1]
```
 Can't assign to an index that doesn't exist (e.g. `x[100]` on a 3-item list raises `IndexError`).

### Deleting Elements — `del`
```python
names = ['Alice', 'Beth', 'Cecil', 'Dee-Dee', 'Earl']
del names[2]    # names -> ['Alice', 'Beth', 'Dee-Dee', 'Earl']
```
Length shrinks by 1. `del` also works on dict entries and variables.

### Slice Assignment
Replace a slice — lengths don't need to match:
```python
name = list('Perl')
name[2:] = list('ar')      # ['P', 'e', 'a', 'r']

name = list('Perl')
name[1:] = list('ython')   # ['P', 'y', 't', 'h', 'o', 'n']
```

**Insert** (assign into an empty slice):
```python
numbers = [1, 5]
numbers[1:1] = [2, 3, 4]   # [1, 2, 3, 4, 5]
```

**Delete a slice** (assign empty list = `del numbers[1:4]`):
```python
numbers = [1, 2, 3, 4, 5]
numbers[1:4] = []          # [1, 5]
```
