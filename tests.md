# Tests

Tests are a way to make sure the software is working as intended, bug-free, without security vulnerabilities and to know its limits.

They also serve as documentation on _how to use the code_

## Types Of Testing

- Functional test: Checks that the software works that way it is supposed to.
    - [Unit test](#unit-tests): Verifies small units of code such as a single methods or functions
    - [Integration test](#integration-tests): Verifies modules or classes interact with each other as supposed to
- [Benchmarks](#benchmarks): Test the performance of the software
- [Fuzzing](#fuzzing): Send random inputs to the software to hopefully find a mysterious bug.
- [Security test](#security-tests): Look for vulnerabilities in the software

## Unit Tests

Tests should be:

- Independent of the environment (except library dependencies)
- Fast
- Parallelizable
- Executed frequently

### TODO_CODE - Write In Temporary Directory

Mosts tests should be read-only regarding the OS environment filesystem.

If writes are necessary, they should be done in a temporary directory that is cleaned up upon test completion or interruption.

If the written files or directories remains, they should not break the next tests execution.

## Integration Tests

## Benchmarks

## Fuzzing

## Security Tests
