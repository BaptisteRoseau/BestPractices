# Tests

Tests are a way to make sure the software is working as intended, bug-free, without security vulnerabilities and to know its limits.

They also serve as documentation on _how to use the code_

## Types of testing

- Functional test: Checks that the software works that way it is supposed to.
    - [Unit test](#unit-tests): Verifies small units of code such as a single methods or functions
    - Integration test: Verifies modules or classes interact with each other as supposed to
- Benchmarks: Test the performance of the software
- Fuzzing: Send random inputs to the software to hopefully find a mysterious bug.
- Security test: Look for vulnerabilities in the software

## Unit tests

Tests should be:

- Independent of the environment (except library dependencies)
- Fast
- Parallelizable
- Executed frequently

### TODO_CODE - Keep it small
