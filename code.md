# Code

## Naming

Naming is important to improve consistency and readability of a code base.

Your team should agree on conventions for the most used object types in your project.

When used consistently, the following rules improve by __a lot__ code readability.

### TODO_CODE - Use full words

Instead of using abbreviations or single letters, use a full word instead.

DO:

```python
start = time.time() 
```

DON'T:

```python
s  = time.time()
```

Abbreviations and single letter are acceptable only:

- in very small functions (1-4 lines)
- by conventions: `i` or `k` for iterators for example
- by written conventions used by your team

This rule is even more necessary for API, functions's arguments and files.

### TODO_CODE - Don't use the type of a variable in its name

DO:

```python
start = 0
```

DON'T

```python
start_timestamp = 0
```

This improves readability by using shorter names, and avoid variables names lying when their types needs an update but the name is not modified.

### TODO_CODE - Use plural for container objects, and only them

Same as the above rule but this is important enough to be a rule by its own.

A container object is an object tat _contains_ other objects such as a list, a hash map, a vector, a tuple, a queue etc..

DO:

```rust
users: Vector<User> = vec![];
```

DON'T

```rust
userList: Vector<User> = vec![];
```

On the contrary, never use plural for variables that are not container objects. Your IDE is here to help you find the type anyway.

### TODO_CODE - Put units in the variable name

DO:

```rust
duration_s: u64 = 60;
```

DON'T

```rust
duration: u64 = 60; // seconds
```

This allows the reader to know the variable unit wherever he reads it instead of having to jump back to its definition.

### TODO_CODE - Use meaningful names

Variables represent _something_. You should __always__ try to boil down _what_ is that concept and write it in the variable name.

Avoid `data`, `value` or naming a variable by its type by all cost.

DO:

```c
int* checkpoints = malloc(CHECKPOINTS_LENGTH*sizeof(int))
```

DON'T:

```c
int* data = malloc(DATA_LENGTH*sizeof(int))
```

There are times where the content of a variable or an attribute is so abstracted that no concept can be found.
In such cases, the use of `data` is perfectly OK.

### TODO_CODE - Use name for variables and attributes, verbs for function

This is more of a general guideline and not an absolute rule.

### TODO_CODE - Use `is_` or `should_` prefix for booleans

DO:

```python
if self.is_ready() and self.should_run:
    self.run()
```

DON'T:

```python
if self.ready() and self.run:
    self.do_run()
```

This avoids confusion between the _actions_ to get ready or run and the _state_ of being ready or the _expected behavior_ of running or not.

## Writing

### TODO_CODE - Top down architecture

### TODO_CODE - Small functions

## Documentation

Documentation
