# Go lang is struct
Go言語ではstructという構造体を定義する文法があります  

## 定義
```go
type Gos struct {
    x, y int
}
```

## 使用
```go
gos  := Gos{1, 2}
p := &gos
p.x = p.x * 2  // (*p).xと書くのは面倒なので、素のまま使用して代入できるようになっている
fmt.Printf("%d¥n", p.x)
```

## 応用
```go
var (
    v1 = Gos{1, 2}
    v2 = Gos{x: 1}  // y is 0
    v3 = Gos{}  // x is 0 and y is 0
    p := &Gos{x: 1, y: 2}
)
```
