# Project Management

## Project Workflow

### PMAP001 - Project Phases

1. Gather feedback on the most needed feature from users
1. Specify __what__ is needed by the users in details
1. Specify __how__ it can be done by the technical team
1. Specify __the interface__ between the user and the implementation details (API)
1. __Mock__ the interface to allow all parties to work in parallel
1. __Implement__ the API endpoints, improve it if necessary
1. __Test__ the API endpoints
1. __Document__ the feature by re-using the specifications
1. __Deliver__ the feature, gather feedback from the users and repeat

## Conventions

Conventions help your code being consistent.

### PMAC001 - Build A Glossary

When a project becomes complex, some concepts or objects may be called differently by different teams.

For example, for a movie streaming company, a _movie_ could be called:

- _A film_ by the business team
- _The raw data_ by the technical team
- _The project_ by the producer
- _The S3 objects_ by the infrastructure team

You may have already lived some confusion because of inconsistent naming.
This is why companies need to build a glossary to ensure that everybody use the same term for these objects (ex: _movie_).

It improves both internal and external communications.

## Source Management

### PMAS001 - Use Git

You should use a version control tool to store your source code, such as Git.

Next: [Productivity](./productivity.md)
