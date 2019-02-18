title: Middleware
---

Middleware provide a convenient mechanism for filtering HTTP requests entering your application. You only need to implement the `Middleware` interface.

```go
route.Get("/foo", func(request *context.Request) *context.Response {
	return thinkgo.Text("Hello ThinkGo !")
}).Middleware(func(request *context.Request, next router.Closure) interface{} {
	if _, err := request.Input("name"); err != nil {
		return thinkgo.Text("Invalid parameters")
	}
	return next(request)
})
```

#### Before Middleware

Whether a middleware runs before or after a request depends on the middleware itself. For example, the following middleware would perform some task `before` the request is handled by the application:

```go
func(request *context.Request, next router.Closure) interface{} {
	
	// Perform action	
	// ...
	
	return next(request)
}
```

#### After  Middleware

However, this middleware would perform its task `after` the request is handled by the application:

```go
func(request *context.Request, next router.Closure) interface{} {
	
	response := next(request)
	
	// Perform action	
	// ...
	
	return response
}
```
