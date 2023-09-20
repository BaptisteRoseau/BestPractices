# Software Architecture

## Generalities

### SARG001 - Use Interfaces

Write your business logic using abstract objects.

Almost every time you need interactions between objects, you should specify how they interact with each other using interfaces.

The use of interfaces is great for at least:

- Maintainability
- Replacing legacy code (as long as the interface remains)
- Hiding implementation
- Testing through mocking
- Select which implementation should be used
- Allow team members to work in parallel

Interfaces can be used everywhere, whether it is in your code, your ticket templates, your web API. Use this rule every time a feature should be provided but the implementation details do not matter.

An interface can be as simple as using the alias `typedef char* Name`, or using a class, a trait or a structure.

If your language provides and interface functionality such as `Interface` in Java, `class` in Python or C++ or `trait` in Rust, use it.
If it provides visibility mechanisms such as `public`, `private` or `protected` in C++, make sure it is used wisely and only the minimum required is public.

### SARG002 - Make Sure You Use Interfaces

Just to make sure you don't forget [SARG001](#sarg001---use-interfaces)

### SARG003 - Business Logic Comes First

When writing a piece of software, the user needs to come first, not the implementation difficulty. Trade-off could be made to reduce the scope.

1. Discuss exactly what the user need is.
1. Extract the main objects used by the business logic.
1. Specify how those objects interact with each other (their __interfaces__)
1. What are the inputs and outputs of the business logic using those objects.

Then, write the business logic using those objects _as if_ they were already implemented.

### SARG004 - Avoid Side Effects

Side effect are evil because they hide you current environment before and after calling the function - regardless of the return value of course.

If done badly, side effects can be a real nightmare to debug, especially if they are not clearly documented.

They can of course be used _within_ an object, for example a `set_ready()` method may modify an object attribute, which is a side effect within an object of a class.

There are some languages such as `Rust` that do a wonderful job at telling the programmer that a side effect can occur on a function parameter by specifying its mutability.

### SARG005 - Add feature flags

When adding a new feature, add a mechanism allowing to enable or disable this feature very easily: with a configuration value or an API call for example.

This allows:

- To quickly disable it in production if a problem happens
- To enable it only to a subset of user, for feedback purposes
- To allow the user to disable the feature if necessary

To do so, one can either add a boolean in a configuration file or database, or an array listing enabled features for example.

## Parallelization

### SARP001 - Always Consider Instruction Being Executed At The Same Time

When writing parallel code, always consider that every single instruction can be executed at the same time.

For example, `i++` in C is at least 3 different instructions:

- read `i`
- increment its value
- write the updated value into `i`

This means that two threads can increment at the same time, and if `i` equals 3 and is incremented two times, then it can become `4` instead of 5.

This is the trivial example of race condition used everywhere but more complex bugs can be avoided by applying this rule consistently.

### SARP002 - Protect Critical Paths

_Critical Paths_ are lines of code that should not be executed in parallel, for example incrementing a counter.

Such lines should be protected using at least:

- atomic instructions: if the instruction is simple enough to have an atomic version.
- locks and mutex: if no atomic instruction exists for the use case, but deadlocks must be avoided.
- parallelizable ADT: if such a structure can be used or written.

A parallelizable ADT (_abstract data type_) is an ADT which interface can be implemented to run in parallel, if possible without locks.

For example, a linked list can be fully parallelizable using only atomic instruction in the critical paths, except for its memory management which requires locks.

### SARP003 - Separate Read And Write Operation

Read operations can usually be done in parallel, whereas it can be difficult to parallelize write operations.

Separating those operations can result in much faster and scalable read operations, at the cost of less frequent update.

Even if not parallel at first, separate these operations allows reducing refactor when scalability will become necessary.

Next: [Tests](./tests.md)
