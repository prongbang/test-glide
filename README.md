# Using -> Glide: Vendor Package Management for Golang

### 1. Install Glide
https://github.com/Masterminds/glide
> On Mac or Linux
```bash
$ curl https://glide.sh/get | sh
```

> On Mac OS X
```bash
$ brew install glide
```

### 2. Initial your project
```bash
$ glide init
```
> Output
```
my-project
├── glide.yaml
```

### 3. Get a package and add to glide.yaml
```bash
$ glide get github.com/gin-gonic/gin
```
> Output
```
my-project
├── glide.lock
├── glide.yaml
└── vendor
├── github.com
    │   ├── gin-gonic
    │   │   └── gin
    │   │       ├── ...
    ...
```
### 4. Install packages and dependencies
```bash
$ glide install
```

### 5. create file main.go
```go
package main

import "github.com/gin-gonic/gin"

func main() {
	gin.SetMode(gin.ReleaseMode)
	r := gin.Default()
	r.GET("/ping", func(c *gin.Context) {
		c.JSON(200, gin.H{
			"message": "pong",
		})
	})
	r.Run() // listen and serve on 0.0.0.0:8080
}
```
> Output
```
my-project
├── README.md
├── glide.lock
├── glide.yaml
├── main.go
└── vendor
```

### 6. run
```bash
$ go run main.go
```

### 7. Open browser
> [http://localhost:8080/ping](http://localhost:8080/ping)