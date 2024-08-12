---
date: "2015-03-08T13:47:32+01:00"
slug: "moving-to-hugo"
tags: ["hugo", "golang", "appengine", "blog"]
title: "Moving to Hugo"
toc: false
readTime: true
autonumber: false
---

It is only a matter of time before I create a static blog. If not for anything, writing in [Markdown](http://daringfireball.net/projects/markdown/syntax) is more comfortable for a coder.

There are many static sites generator but the one I fell in love with is [Hugo](http://gohugo.io) probably because of my bias for [Go](http://golang.org) ;).

Hopefully, it will influence my blogging frequency.

### Hosting on App Engine

Go is dead simple to create a file server and a line of code like this `http.Handle("/", http.FileServer(http.Dir("public")))` is all you need.

To host a static site on [AppEngine](http://cloud.google.com/appengine) using Go, we need 2 files `app.yaml` and `main.go`.

Put this in `app.yaml`.

```yaml
application: staticsite
version: 1
runtime: go
api_version: go1

handlers:
- url: /.*
  script: _go_app
```
And this in `main.go`.

```go
package main

import "net/http"

func init() {
	http.Handle("/", http.FileServer(http.Dir("public")))
}
```

Then let us run `hugo` with the `-d` flag specifying the directory to put the generated static contents.

```sh
$ hugo -d /path/to/appengine/project/public
```

And finally start our local appengine server.

```sh
$ goapp serve /path/to/appengine/project
```

Pretty cool, isn't it.
