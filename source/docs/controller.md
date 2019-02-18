title: Controller
---

#### Basic Controller

Below is an example of a basic controller class.

```go
package controller

import (
	"github.com/thinkoner/thinkgo"
	"github.com/thinkoner/thinkgo/context"
)

func Index(req *context.Request) *context.Response {
	return thinkgo.Text("Hello ThinkGo !")
}

```

You can define a route to this controller like so:

```go
route.Get("/", controller.Index)
```

#### Resource Controller

This feature will be supported in a future release.