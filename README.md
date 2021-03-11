# plox
## Plan 9, but everything is request and response

### Requirements

* Requests may contain any data
* Responses may contain any data
* Requests must be less than or equal to 4MiB in size
* Requests should be less than or equal to 4MB in size
* Receivers must be a resource type and path with no query parameters. For example `file:/usr/bin/ploxgrep` or `https:api.example.com/some/resource/here`
* Responses must be returned within 15s
* Responses should be returned within 10s
* The client should assume that if 15s have elapsed since the request was sent that the request has failed

## Implementation methods

### Processes

An executable file is executed with no options or arguments, and stdin containing all request data including data that would typically be considered "options".

Chunking will need to be implemented to support input data larger than 4 megabytes.

May be implemented in terms of existing commands which do take options.

This method is not *Open Group Base Specifications* compliant.

This method is portable.

### QUIC or HTTPS

POST data representing a request to a URL containing no query parameters, and body containing all request data including data that would typically be considered "query parameters".

Chunking will need to be implemented to support input data larger than 4 megabytes.

May be implemented in terms of other requests, such as GET or HEAD, or POST with parameters in the query string.

This method is not REST-ful.

This method is compatible with HTTP 1, 2 and 3, QUIC, JSON, GraphQL.

## Authentication and Authorization

* Cryptographic, authentication and authorization (authz) data must have appropriate expiration times set
* authz data sent to the receiver should be outside of the request or path
  * For example, it may instead be sent via HTTP Authorization header, or via file descriptor number 3
  * Discretionary Access Control may be implemented using paths containing authz data
* authz data may be contained within the response body
* Secrets data (such as passwords and API keys) should be used only to retrieve authz data
* Secrets data may be sent in the request body
