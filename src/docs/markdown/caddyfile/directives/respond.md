---
title: respond (Caddyfile directive)
---

# respond

Writes a hard-coded/static response to the client.


## Syntax

```
respond [<matcher>] <status>|<body> [<status>] {
	body <text>
	close
}
```

- **&lt;status&gt;** is the HTTP status code to write. Default 200.
- **&lt;body&gt;** is the response body to write.
- **body** is an alternate way to provide a body; convenient if it is multiple lines.
- **close** will close the client's connection to the server after writing the response.

To clarify, the first non-matcher argument can be either a 3-digit status code or a response body string. If it is a body, the next argument can be the status code.


## Examples

Write a 200 status with an empty body to all health checks:

```
respond /health-check 200
```

Write a simple response body to all requests:

```
respond "Hello, world!"
```

Write an error response and close the connection:

```
respond /secret/* "Access denied" 403 {
	close
}
```
