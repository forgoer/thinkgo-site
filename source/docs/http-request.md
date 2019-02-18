title: HTTP Request
---
#### Accessing The Request

To obtain an instance of the current HTTP request via dependency injection

```go
func Handler(req *context.Request) *context.Response {
	name := req.Input("name")
}
```

#### Dependency Injection & Route Parameters

If your controller method is also expecting input from a route parameter you should list your route parameters after the request dependencies. For example, you can access your route parameter `name` like so:

```go
route.Put("/user/{name}", func(req *context.Request, name string) *context.Response {
	//
})
```

#### Request Path & Method

The `path` method returns the request's path information. So, if the incoming request is targeted at `http://domain.com/foo/bar`, the `path` method will return `foo/bar`:

```go
uri := req.GetPath()
```

The `method` method will return the HTTP verb for the request. 

```go
method := req.GetMethod();
```

#### Retrieving Cookies From Requests

```go
name, _ := request.Cookie("name")
```