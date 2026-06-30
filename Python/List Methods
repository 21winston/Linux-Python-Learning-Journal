# Python Lists & Tuples

## List methods

| Method | What it does | Changes the list? | Returns |
|---|---|---|---|
| `lst.append(x)` | Adds x to the end | Yes | None |
| `lst.extend(seq)` | Adds all items from seq to the end | Yes | None |
| `lst.insert(i, x)` | Inserts x at index i | Yes | None |
| `lst.pop(i)` | Removes and returns item at index i (default last) | Yes | The removed item |
| `lst.remove(x)` | Removes the first match of x, errors if not found | Yes | None |
| `lst.clear()` | Empties the list | Yes | None |
| `lst.index(x)` | Finds the index of the first match of x, errors if not found | No | Index |
| `lst.count(x)` | Counts how many times x appears | No | Count |
| `lst.sort()` | Sorts the list | Yes | None |
| `lst.reverse()` | Reverses the list | Yes | None |

Non-mutating alternatives:
- `sorted(lst)` returns a new sorted list, original untouched
- `list(reversed(lst))` returns a new reversed list, original untouched

## The in-place trap

`.sort()`, `.append()`, and similar methods change the list directly and return `None`. Don't assign the result to a variable.

```python
x = [4, 2, 3]
y = x.sort()  # y is None, not the sorted list
```

## Assignment vs copying

`b = a` doesn't copy a list, it just points b to the same list as a. Changing one changes both.

To get an actual independent copy, use `.copy()`, slicing `[:]`, or `list()`.

```python
a = [1, 2, 3]
b = a         # b and a are the same list
c = a.copy()  # c is a separate list
```

## Stack and queue with lists

- Stack (LIFO): `append(x)` to push, `pop()` to pop
- Queue (FIFO): `append(x)` to add, `pop(0)` to remove from the front (for real queues, use `collections.deque` instead, it's faster)

## Tuples

Tuples work like lists but can't be changed after creation.

A one-item tuple needs a trailing comma:

```python
not_a_tuple = (42)   # just the integer 42
a_tuple = (42,)       # a tuple with one item
```

Why use a tuple over a list:
- Protects data from being changed by accident
- Can be used as a dictionary key or set member, lists can't
