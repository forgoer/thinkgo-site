title: Routing
---

#### Basic Routing

The most basic routes accept a URI and a Closure, providing a very simple and expressive method of defining routes:

```go
app.RegisterRoute(func(route *router.Route) {
	route.Get("/foo", func(req *context.Request) *context.Response {
		return thinkgo.Text("Hello ThinkGo !")
	})
})
```

#### Available Router Methods

The router allows you to register routes that respond to any HTTP verb:

```go
route.Get("/someGet", getting)
route.Post("/somePost", posting)
route.Put("/somePut", putting)
route.Delete("/someDelete", deleting)
route.Patch("/somePatch", patching)
route.Options("/someOptions", options)
```

Sometimes you may need to register a route that responds to multiple HTTP verbs. You may even register a route that responds to all HTTP verbs using the `Any` method:

```go
route.Any("/someAny", any)
```

#### Parameters in path

Of course, sometimes you will need to capture segments of the URI within your route. For example, you may need to capture a user's ID from the URL. You may do so by defining route parameters:

```go
route.Get("/user/{id}", func(req *context.Request, id string) *context.Response {
	return thinkgo.Text(fmt.Sprintf("User %s", id))
})
```

You may define as many route parameters as required by your route:

```go
route.Get("/posts/{post}/comments/{comment}", func(req *context.Request, postId, commentId string) *context.Response {
	//
})
```

#### Route Prefixes

The prefix method may be used to prefix each route in the group with a given URI. For example, you may want to prefix all route URIs within the group with `admin`:

```go
route.Prefix("/admin").Group(func(group *router.Route) {
	group.Prefix("user").Group(func(group *router.Route) {
	    // ... 	
	})
	group.Prefix("posts").Group(func(group *router.Route) {
		// ... 	
    })
})
```

#### Route Groups

Route groups allow you to share route attributes, such as middleware or prefix, across a large number of routes without needing to define those attributes on each individual route.

```go
route.Prefix("/admin").Group(func(group *router.Route) {
	group.Prefix("user").Group(func(group *router.Route) {
		group.Get("", func(request *context.Request) *context.Response {
			return thinkgo.Text("admin user !")
		}).Middleware(func(request *context.Request, next router.Closure) interface{} {
			if _, err := request.Input("id"); err != nil {
				return thinkgo.Text("Invalid parameters")
			}
			return next(request)
		})
		group.Get("edit", func(request *context.Request) *context.Response {
			return thinkgo.Text("admin user edit !")
		})
	}).Middleware(func(request *context.Request, next router.Closure) interface{} {
		if _, err := request.Input("user"); err != nil {
			return thinkgo.Text("Invalid parameters")
		}
		return next(request)
	})
}).Middleware(func(request *context.Request, next router.Closure) interface{} {
	if _, err := request.Input("token"); err != nil {
		return thinkgo.Text("Invalid parameters")
	}
	return next(request)
})
```