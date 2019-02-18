title: Logging
---

The logger provides the eight logging levels defined in [RFC 5424]( https://tools.ietf.org/html/rfc5424 ): **emergency**, **alert**, **critical**, **error**, **warning**, **notice**, **info** and **debug**.

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