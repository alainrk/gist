# Go

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

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```

### XXX
```go
```
