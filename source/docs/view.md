title: View
---
views are stored in the `views` directory, A simple view might look something like this:

`views/layout.html` like this:

```html
{{ define "layout" }}
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>{{ .Title }}</title>
</head>
<body>
	{{ template "content" .}}
</body>
</html>
{{ end }}
```

`views/tpl.html` like this:

```html
{{ define "content" }}
<h2>{{ .Message }}</h2>
{{ end }}
{{ template "layout" . }}
```

we may return it using the `Render` function like so:

```go
route.Get("/tpl", func(request *context.Request) *context.Response {
	data := map[string]interface{}{"Title": "ThinkGo", "Message": "Hello ThinkGo !"}
	return thinkgo.Render("tpl.html", data)
})
```