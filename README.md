# plox
## Like Plan 9, but everything is request and response

### Requirements

* Requests may contain any data
* Responses may contain any data
* Requests must be less than or equal to 4MiB in size
* Requests should be less than or equal to 4MB in size
* Receivers must be a resource type and path with no query parameters. For example `file:/usr/bin/ploxgrep` or `https:api.example.com/some/resource/here`
* Responses must be returned within 15s
* Responses should be returned within 10s

## Implementation methods

### Processes

An executable file is executed with no options or arguments, and stdin containing all request data including data that would typically be considered "options".

Chunking may need to be supported for input data larger than 4 megabytes.

May be implemented in terms of existing commands which do take options.

### QUIC or HTTPS

POST data representing a request to a URL containing no query parameters.

May be implemented in terms of other requests, such as GET or HEAD, or POST with parameters in the query string.

This method is not REST-ful.

This method is compatible with GraphQL.
