# Go lang is range
Go言語にはrangeというmapをforループさせるための文があります。  

```go
a := []int{10, 20, 30}
for i, v := range a {
    fmt.Printf("%d: %d¥n", i, v)  // 0:10 1:20 2:30
}
```
