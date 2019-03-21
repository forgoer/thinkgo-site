title: Logging
---

The logger provides the eight logging levels defined in [RFC 5424]( https://tools.ietf.org/html/rfc5424 ): **emergency**, **alert**, **critical**, **error**, **warning**, **notice**, **info** and **debug**.

#### Basic Usage

```go
import "github.com/thinkoner/thinkgo/log"

log.Debug("log with Debug")
log.Info("log with Info")
log.Notice("log with Notice")
log.Warn("log with Warn")
log.Error("log with Error")
log.Crit("log with Crit")
log.Alert("log with Alert")
log.Emerg("log with Emerg")
```

#### Log Storage

Out of the box, ThinkGo supports writing log information to `daily` files, the `console`.

For example, if you wish to use `daily` log files, you can do this: 

```go
import (
	"github.com/thinkoner/thinkgo/log"
	"github.com/thinkoner/thinkgo/log/handler"
	"github.com/thinkoner/thinkgo/log/record"
)

fh := handler.NewFileHandler("path/to/thinkgo.log", record.INFO)

log.GetLogger().PushHandler(fh)
```
