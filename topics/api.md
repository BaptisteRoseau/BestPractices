# API

## Generalities

### APIG001 - Don't Break The API

Never silently break an API over a release.

The REST standards advise using versioning in your Web API, for example using a `/v1` route prefix.

When a breaking change is introduced in the API (parameter renaming, route path renaming, etc.), you should mark what changed as _Deprecated_ either in the `Warning` or in the `Deprecation` HTTP Header and keep the deprecated item over at least a release.

- If you only add features: no need to upgrade the version.
- If you rename a route's parameter: allow the use of the deprecated parameter but mark it as deprecated when used.
- If you rename a route: allow the use of the deprecated route, mark it as deprecated, return an HTTP status code 300, and redirect the call to the expected route.
- If all the routes and parameters change: this is a new API. Upgrade the version prefix to `/v2` and mark all the `/v1` routes as deprecated.

When having a full API upgrade, organize your codebase in order to have all of the previous versions in a single file or folder to only have to remove it when the time comes.

This rule does not apply to products still being in beta.

## Web APIs

### APIW001 - Pagination

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

### APIW002 - Use Standards

Currently, the most widely used standards are:

- SOAP
- REST
- GraphQL
- gRPC/Protocol Buffer

Most web APIs use REST for its simplicity.
For data access, organizations are transitioning towards GraphQL.
For internal services, use gRPC or Protocol Buffer for its performance.

### APIW003 - Naming

Naming in APIs is absolutely crucial and the [Code Naming](./code.md#naming) best practices apply best in Web API.

The things that can be named are:

- routes
- query parameters
- query body keys

Your API must be clear, simple, documented, and well-named. Remember that your public API is how users will use your product and perceive your organization. A poorly designed API means you are a poorly organized organization.

Next: [Software Architecture](./software_architecture.md)
