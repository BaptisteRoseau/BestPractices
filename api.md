# API

## Generalities

### TODO_CODE - Don't break the API

Never silently break an API over a release.

The REST standards advise using versioning onto you Web API

## Web APIs

### TODO_CODE - Pagination

For pagination, use at least the pattern `first`, `last`, `from`, `amount`.

It gives indexes to the first and the last elements as well as the length of the list, and also the amount of items we want to retrieve from a specific included item.

Example:

```json
{
    "first": "MA==",
    "last": "MjU1",
    "length": 254,
    "from": "NjQ=",
    "amount": 15
}
```

Because the indexes are iterators, we abstract their value using base64 to avoid the user using the numeric index and ease a change in the iterator without breaking the API.

Note that this is subject to improvement, but there are numbers of pagination best practices on the internet only waiting for you to read them.

### TODO_CODE - Use standards

<!-- TODO: links -->

Currently the most widely used standards are:

- SOAP
- REST
- GraphQL
- gRPC/Protocol Buffer

Most web APIs use REST for its simplicity.
For data access, organizations are transitioning towards GraphQL.
For internal services, use gRPC or Protocol Buffer for its performance.

### TODO_CODE - Naming

Naming in APIs is absolutely crucial and the [Code Naming](./code.md#naming) best practices apply best in Web API.

Your API must be clear, simple, documented and well named. Remember that your public API is how users will use your product and perceive your organization. A crappy API means you are a crappy organization.
