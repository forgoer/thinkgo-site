title: Cache
---
ThinkGo Cache Currently supports redis, memory, and can customize the store adapter.

#### Basic Usage

```go
import (
	"github.com/thinkoner/thinkgo/cache"
	"time"
)


var foo string 

// Create a cache with memory store
c, _ := cache.Cache(cache.NewMemoryStore("thinkgo"))

// Set the value
c.Put("foo", "thinkgo", 10 * time.Minute)

// Get the string associated with the key "foo" from the cache
c.Get("foo", &foo)

```

#### Retrieve & Store

Sometimes you may wish to retrieve an item from the cache, but also store a default value if the requested item doesn't exist. For example, you may wish to retrieve all users from the cache or, if they don't exist, retrieve them from the callback and add them to the cache. You may do this using the `Remember` method:

```go
var foo int

cache.Remember("foo", &a, 1*time.Minute, func() interface{} {
	return "thinkgo"
})
```

refer to [ThinkGo Cache]( https://github.com/thinkoner/thinkgo/tree/master/cache )
