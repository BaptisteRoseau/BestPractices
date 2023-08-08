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

When using a language that allows it, write the public methods and public functions at the top of the class or the module.

This allows the reader to look as the available public code faster and hide the implementations details bellow, available to read only if necessary.

### TODO_CODE - Small functions

A function should have a single purpose.

High level functions such as the `main` can be large, but the more you dive into implementation, the smaller the function should be.

However, don't fall into the mistake of making too many small functions.
It will reduce readability because it requires too much back and forth between functions implementations.

In general, use 2 levels of abstractions for functions or methods, 3 in some cases. If using more then then the module or the class could be refactored into smaller classes or modules.

In general, avoid having functions longer that what can fit in your IDE vertical space. And don't reduce the zoom to bypass this rule.

### TODO_CODE - Comments

TODO

### TODO_CODE - Remove commented code

Commented code should be removed. If it is very important to keep it, add a commentary with the commit hash that removes the "functionality" provided but the commented code.

## Documentation

### TODO_CODE - Specifications & API First

Specification should be done __before__ the project code is being written. Most importantly, the __API specification__ should be discussed and tailored before the implementation begins.

The specifications can often be used as the raw material for the documentation. A few adjustments generally have to be made, but if the specifications are great, the code is great, and the documentation at least exists.

### TODO_CODE - Code Documentation

Code documentation should be written directly into the code, using docstring or a third party tool like Doxygen. Not every function requires it, but all the public functions of a class or module should be commented.

Example:

```python
def is_ready(self) -> bool:
    """ Returns true if the player is ready. """
    return self.preparation >= 1.0
```

- If the function above is private: no need to document it.
- If the function above is public: you should document it using a documentation tool format.

### TODO_CODE - Internal Documentation

Internal documentation is a kind a documentation that is made for developers and infrastructure engineers. It should be visual and simple, containing:

- A class diagram: how do the objects interact with each others
- A data flow diagram: where the data comes from and where it is processed ?
- A quick explanation of how a module is supposed to work and interact with other modules
- Explanations of the tradeoff choices made during the development if any

The last point is critical to avoid making the mistake of taking the wrong path after long brainstorming that already pointed out why this decision has been rejected.

### TODO_CODE - Public Documentation

Public documentation is by far the most important. Being public, it reflects the quality of your product, regardless of the code.