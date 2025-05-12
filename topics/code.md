# Code

## Naming

Naming is important to improve consistency and readability of a code base.

Your team should agree on conventions for the most used object types in your project.

When used consistently, the following rules improve by __a lot__ code readability.

### CODN001 - Use Full Words

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

- by conventions: `i` or `k` for iterators for example
- by written conventions used by your team

This rule is even more necessary for API, functions's arguments and file names.

### CODN002 - Don't Use The Type Of A Variable In Its Name

DO:

```python
start = 0
```

DON'T

```python
start_timestamp = 0
```

This improves readability by using shorter names, and avoid variable names lying when their types needs an update but their name is not modified.

Don't worry your IDE is here to help you find the type and with auto completion.

### CODN003 - Use Plural For Container Objects, And Only Them

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

On the contrary, never use plural for variables that are not container objects.

Queues and stacks may sometimes be singular in specific cases.

### CODN004 - Put Units In The Variable Name

DO:

```rust
duration_s: u64 = 60;
```

DON'T

```rust
duration: u64 = 60; // seconds
```

This allows the reader to know the variable unit wherever he reads it instead of having to jump back to its definition.

### CODN005 - Use Meaningful Names

Variables represent _something_. You should __always__ try to boil down _what_ is that concept and write it in the variable name.

Avoid `data`, `value` or naming a variable by its type.

DO:

```c
int* checkpoints = malloc(CHECKPOINTS_LENGTH*sizeof(int))
```

DON'T:

```c
int* data_array = malloc(DATA_LENGTH*sizeof(int))
```

There are times where the content of a variable or an attribute is so abstracted that no concept can be found. In such cases, the use of `data` is perfectly OK.

### CODN006 - Use Name For Variables And Attributes, Verbs For Function

This is more of a general guideline and not an absolute rule.

### CODN007 - Use Verbs Prefix Like `is_` Or `should_` For Booleans

DO:

```python
if self.is_ready() and self._should_run:
    self.run()
```

DON'T:

```python
if self.ready() and self.run():
    self.do_run()
```

This avoids confusion between:

- the _actions_ to get ready and run
- the _state_ of being ready
- the _expected behavior_ of running or not

## Writing

### CODW001 - Top Down Organization

When using a language that allows it, write the public methods and public functions at the top of the class or the module.

This allows the reader to look at the available public code faster and hide the implementations details bellow, available to read only if necessary.

### CODW002 - Keep Dependencies Close

Code that uses a function within the same module should be close to the called function in terms of lines.

### CODW003 - Small Functions

Functions should have a single purpose.

High level functions such as the `main` can be large, but the more you dive into implementation, the smaller the function should be.

However, don't fall into the mistake of making too many small functions.
It reduces readability because it requires too much back and forth between functions implementations.

In general, use 2 levels of abstractions for functions or methods, 3 in some cases. If using more then the module or the class could be refactored into smaller classes or modules.

In general, avoid having functions longer that what can fit in your IDE vertical space. And don't reduce the zoom to bypass this rule.

Another exception to this rule is when a very high level of optimization is required for a specific function.

### CODW004 - Use Affirmative In Conditional Statements

DO:

```rust
if player.is_ready(){
    player.play()
}
```

DON'T

```rust
if !player.is_busy(){
    player.play()
}
```

This ease the reading of the conditional statement.

This rule is not absolute. Negative conditional statement are perfectly fine, but when the programmer has the choice, affirmative conditional statements should be chosen.

### CODW005 - Comments

Avoid writing comments.

If you find yourself writing a commend above a block of code, write this block of code in a __function__ instead.

Comments are useful to explain tradeoff, but they tend to be:

- unread
- forgotten
- lying

So, avoid them.

### CODW006 - Remove Commented Code

Commented code should be removed.

If it is very important to keep it, add a commentary with the commit hash that removes the "functionality" provided but the commented code, or actually implement the functionality.

### CODW007 - Don't Optimize At First

Performance is important but should not be considered __before__ implementing a feature. The code should be __simple__, __readable__ and __maintainable__ before being __performant__.

In IT, everything is a trade off, and usually, the first implementation is performant enough to avoid the need of optimization.

Optimizing too early in the implementation can highly reduce maintainability and readability for a small performance gain.

Always optimize your software bottleneck before optimizing features not implemented yet.

### CODW008 - TODOs

`TODO` comments can be used while developing as a marker of an idea or work to be done.

However, they have to be implemented before getting to the code review or being merged. Especially if it take 5min to 10min to implement.

Whenever you find yourself writing a TODO, implement it on the go if it is short enough.

Longer TODOs, such as a full feature can be kept in the codebase, however it is a better practice to write a ticket with the specification of what needs to be done.

## Documentation

### CODD001 - Specifications

Specification should be done __before__ the code is written. Most importantly, the __API specification__ should be discussed and tailored before the implementation begins.

The specifications can often be used as the raw material for the documentation. A few adjustments generally have to be made, but if the specifications are great, the code is great, and the documentation at least exists.

### CODD002 - Code Documentation

Code documentation should be written directly into the code, using docstring or a third party tool like Doxygen. Not every function requires it, but all the public functions of a class or module should be documented.

Example:

```python
def is_ready(self) -> bool:
    """ Returns true if the player is ready. """
    return self.preparation >= 1.0
```

- If the function above is private: no need to document it.
- If the function above is public: you should document it using a documentation tool format.

### CODD003 - Internal Documentation

Internal documentation is a kind a documentation that is made for developers and infrastructure engineers. It should be visual and simple, containing:

- A class diagram: how do the objects interact with each others
- A data flow diagram: where the data comes from and where it is processed ?
- A quick explanation of how a module is supposed to work and interact with the others
- Explanations of the trade off choices made during the development if any

The last point is critical to avoid making the mistake of taking the wrong path after long brainstorming that already pointed out why this decision has been rejected.

### CODD004 - Public Documentation

Public documentation is by far the most important. Being public, it reflects the quality of your product, regardless of the code.

Next: [API](./api.md)
