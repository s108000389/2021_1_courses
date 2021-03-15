#
```
Mastering Go - Second Edition
By Mihalis Tsoukalos
https://www.packtpub.com/product/mastering-go-second-edition/9781838559335
```

# ch1
```
FROM golang:alpine

RUN mkdir /files
COPY hw.go /files
WORKDIR /files

RUN go build -o /files/hw hw.go
ENTRYPOINT ["/files/hw"]
```
```
package main

import (
	"fmt"
)

func main() {
	fmt.Println("Hello World!")
}
```
