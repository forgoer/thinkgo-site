title: HTTP Response
---
an HTTP Response Must implement the `*context.Response` interface

#### Creating Responses

a simple strings or json Response:

```go
thinkgo.Text("Hello ThinkGo !")

thinkgo.Json(map[string]string{
				"message": "pong",
			})
```

#### Attaching Cookies To Responses

```go
response.Cookie("name", "alice")
```

#### Redirects

```go
route.Get("/redirect", func(request *context.Request) *context.Response {
	return context.Redirect("https://www.google.com")
})
```