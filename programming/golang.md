# Go

## Interfaces and structs

### Embedding a struct
Useful to test libraries or in general functions taking interfaces as parameter without implementing all the methods.
```go
type Printer interface {
  Print(string)
  Setup(int, string) // No need to implement all
}

type Log struct {
  prefix string
  Printer // Embed
}

func (l Log) Print(s string) {
  fmt.Printf("%s: %s\n", l.prefix, s)
}

// test takes a Printer, but we don't need to implement what we don't use inside of it
func test(p Printer) {
  p.Print("This is a test") // debug: This is a test
  // p.Setup(4, "hello") // This would raise an error instead
}

func main() {
  l := Log{ prefix: "debug" }
  test(l)
}
```

## Channels

### Stop routine through channel

```go
func routine(stop chan bool) {
  i := 0
  for {
    select {
    case ok := <-stop:
      if ok {
        continue
      }
      return
    default:
      fmt.Printf("%d ", i)
      i++
    }
    time.Sleep(500 * time.Millisecond)
  }
}

func main() {
  stop := make(chan bool)
  go routine(stop)
  for i := 0; i < 10; i++ {
    time.Sleep(1 * time.Second)
    stop <- true
  }
  stop <- false
}

// 0 1 2 3 4 5 6 7 8 9 10 11 12
```

### Close channel
```go
func routine(stop chan bool, done chan bool) {
  i := 0
  for {
    v, ok := <-stop
    fmt.Println(i, v)
    if ok {
      i++
      continue
    } else {
      done <- true
      return
    }
    time.Sleep(500 * time.Millisecond)
  }
}

func main() {
  stop := make(chan bool)
  done := make(chan bool)
  go routine(stop, done)
  for i := 0; i < 5; i++ {
    time.Sleep(1 * time.Second)
    stop <- true
  }
  close(stop)
  <-done
}

// 0 true
// 1 true
// 2 true
// 3 true
// 4 true
// 5 false
```

## Strings, []byte, []rune

### Reverse a string
```go
func reverseR(b []rune) []rune {
	l := len(b)
	if l <= 1 {
		return b
	}
	return append([]rune{b[l-1]}, reverseR(b[:l-1])...)
}

func reverseS(s string) string {
	return string(reverseR([]rune(s)))
}

func main() {
	fmt.Println(reverseS("Hello, 世界!")) // !界世 ,olleH
}
```

## HTTP

## Multiple Servers and Client example
```go
package main

import (
	"fmt"
	"io/ioutil"
	"net/http"
	"os"
	"time"
)

func handleMain(w http.ResponseWriter, r *http.Request) {
	w.Write([]byte("Main page"))
}

func handleMetrics(w http.ResponseWriter, r *http.Request) {
	w.Header().Add("content-type", "application/json")
	w.Write([]byte(fmt.Sprintf(`{ "status": "OK", "date": "%s" }`, time.Now().Format("Mon Jan _2 15:04:05 2006"))))
}

func reqMetrics() {
	for {
		time.Sleep(1 * time.Second)
		requestURL := fmt.Sprintf("http://localhost:8033/metrics")

		req, err := http.NewRequest(http.MethodGet, requestURL, nil)
		if err != nil {
			fmt.Printf("client: could not create request: %s\n", err)
			os.Exit(1)
		}

		res, err := http.DefaultClient.Do(req)
		if err != nil {
			fmt.Printf("client: error making http request: %s\n", err)
			os.Exit(1)
		}

		if res.StatusCode >= 200 && res.StatusCode < 300 {
			resBody, _ := ioutil.ReadAll(res.Body)
			fmt.Println(string(resBody))
		}
	}
}

func main() {
	muxMain := http.NewServeMux()
	muxMetrics := http.NewServeMux()

	muxMain.HandleFunc("/", handleMain)
	muxMetrics.HandleFunc("/metrics", handleMetrics)

  // Simple way to listen on multiple ports
	go http.ListenAndServe(":8033", muxMetrics)
  // Demonstration of requests
	go reqMetrics()
  // Main server
	http.ListenAndServe(":8080", muxMain)
}
```

### Replication of promise.all()
```go
// Source: http://nathan.vegas/blog/errgroup-promise-all.html

var userDetails *user.Details
var userCards []payment.Card
var userPurchases []shop.Purchase

errGroup, groupCtx := errgroup.WithContext(ctx)

errGroup.Go(func() error {
  var err error
  userDetails, err = user.FindDetailsByID(groupCtx, userID)
  return err
})

errGroup.Go(func() error {
  var err error
  userCards, err = payment.FindCardsByUserID(groupCtx, userID)
  return err
})

errGroup.Go(func() error {
  var err error
  userPurchases, err = shop.FindPurchasesByUserID(groupCtx, userID)
  return err
})

err := errGroup.Wait()
if err != nil {
  // ... handle the error
}
```
