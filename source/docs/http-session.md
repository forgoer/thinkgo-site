title: HTTP-Session
---

retrieving Data like this:

```go
request.Session().Get("user")
```

storing Data like this:

```go
request.Session().Set("user", "alice")
```