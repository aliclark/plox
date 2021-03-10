# plox
## Like Plan 9, but everything is request and response

* Requests may contain any data
* Responses may contain any data
* Requests must be less than or equal to 4MiB in size
* Requests should be less than or equal to 4MB in size
* Receivers must be a resource type and path with no query parameters. For example `file:/usr/bin/ploxgrep` or `https:api.example.com/some/resource/here`
* Responses must be returned within 15s
* Responses should be returned within 10s
