title: Documentation
---
Welcome to the ThinkGo documentation. If you encounter any problems when using ThinkGo, have a look at the  [troubleshooting guide](troubleshooting.html), raise an issue on [GitHub](https://github.com/thinkoner/thinkgo/issues).

## What is ThinkGo?

ThinkGo is a fast, simple and powerful web framework written in Go (Golang). That currently supports the basic functionality of web frameworks such as routing, middleware, controllers, requests, responses, sessions, views, logs, caching, ORM, and ThinkGo is committed to making code simple. And expressive, helping developers quickly build a web application.

## Installation

The only requirement is the [Go Programming Language](https://golang.org/dl/). If you encounter a problem and can't find the solution here, please [submit a GitHub issue](https://github.com/thinkoner/thinkgo/issues) and I'll try to solve it.

Just install Hexo with `go get`:

``` bash
$ go get github.com/thinkoner/thinkgo
```

## Quick start

ThinkGo is installed, Start a project quickly:

``` golang
package main

import (
  "github.com/thinkoner/thinkgo"
  "fmt"
  "github.com/thinkoner/thinkgo/router"
  "github.com/thinkoner/thinkgo/context"
)

func main() {
  app := thinkgo.BootStrap()
  app.RegisterRoute(func(route *router.Route) {

    route.Get("/", func(req *context.Request) *context.Response {
      return thinkgo.Text("Hello ThinkGo !")
    })

    route.Get("/ping", func(req *context.Request) *context.Response {
      return thinkgo.Json(map[string]string{
        "message": "pong",
        })
    })

    // Dependency injection
    route.Get("/user/{name}", func(req *context.Request, name string) *context.Response {
      return thinkgo.Text(fmt.Sprintf("Hello %s !", name))
    })
  })
  // listen and serve on 0.0.0.0:9011
  app.Run()
}
```