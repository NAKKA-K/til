# unicode
Go言語でUnicode文字を扱う場合、ASCII文字を扱うときとは少し勝手が違います。  
Unicode文字を簡単に扱う場合は、unicodeパッケージをインポートして扱います。  

## 文字数
len関数は文字数を返すわけではなく、バイト数を返します。  
そのためUnicode文字の文字数が知りたい場合にlen関数を使っても期待通りに文字数は出ません。  
Unicode文字の文字数を正確に出したい場合、Unicodeパッケージ内のメソッドを使用してください。  

```go
import "unicode/utf8"
s := "Hello, 世界"
fmt.Println(len(s))  // 13
fmt.Println(utf8.RuneCountInString(s))  // 9
```

## 文字の処理
Unicode文字を1文字ずつ処理したい場合などは、そのままループで出しても1文字ずつは出ません。  
処理する方法は2つあります。  

```go
for i := 0; i < len(s); {
    r, size := utf8.DecodeRuneInString(s[i:])  // r: ルーン, size: バイト数
    fmt.Printf("%c", r)
    i += size
}
```

```go
for _, r := range s {
    fmt.Printf("%c\n", r)
}
```
