title: ThinkGo 0.1 Released
---

`ThinkGo` is a lightweight MVC framework written in Go (Golang).

## New Features

### Route Prefixes and Groups
- Route Prefixes: The prefix method may be used to prefix each route in the group with a given URI
- Route Groups:  Allow you to share route attributes, such as Middleware or Prefixes

### Middlewares
- Middleware provide a convenient mechanism for filtering HTTP requests entering your application

## Improvement
`thinkgo.Response` is adjusted to `context.Response`

