# new
Go言語の変数宣言では、new組み込み関数を使った変数宣言もあります。  
new関数を使って作成された変数は、作った変数のアドレスを返します。  

```go
p := new(int)
fmt.Println(*p)  // => 0
```
