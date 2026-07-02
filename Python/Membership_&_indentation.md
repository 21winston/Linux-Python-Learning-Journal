# Sequence Membership & Indentation

## `in` operator
Boolean check: is value present in a sequence? `True`/`False`.

```python
'w' in 'rw'                      # True  - substring/char check
'mlh' in ['mlh', 'foo', 'bar']    # True  - element check
```

## List-of-lists matching (e.g. login)

```python
database = [
    ['Albert', '1234'],  # [0]=username, [1]=PIN
    ['Chude',  '4567']
]

if [username, pin] in database:
    print('Access granted')
else:
    print('Access denied')
```

- Python has no concept of "username"/"PIN" — only strings and index positions.
- `[username, pin]` builds a temp list; Python looks for an inner list matching **both elements in order**.
- Swap the inputs (PIN in username field) → Python searches for `['1234', 'Albert']` → no match → denied.
- **Order matters. Always.**

## Indentation

No `{}` blocks — whitespace defines structure.

**Single-line form** (must align `if`/`else` in the same column):
```python
if condition: print('Yes')
else: print('No')
```
One stray space before `else:` → `IndentationError: unexpected indent`.

**Preferred multi-line form** (4-space indent, no alignment risk):
```python
if [username, pin] in database:
    print('Access granted')
else:
    print('Access denied')
```
