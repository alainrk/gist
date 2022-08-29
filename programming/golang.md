# Go

### Embedding a struct
```go
type Printer interface {
	Print(string)
}

type Log struct {
	prefix string
	Printer // Embed
}

func (l Log) Print(s string) {
	fmt.Printf("%s: %s\n", l.prefix, s)
}

func main() {
	l := Log{ prefix: "debug" }
	l.Print("This is a test") // debug: This is a test
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
