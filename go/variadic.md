# 可変個引数
関数の引数などで、可変個の引数を用いて呼び出すことができる構文です。  

可変個引数関数を宣言するには以下のように記述します。  

```go
func print(format string, args ...string){}
```

可変個引数関数を呼び出すには以下のように呼び出します。  

```go
print("test", a, b, c)
print("test")
```

この可変個引数関数の呼び出しは特殊で、可変個の引数をスライスとして受け渡したかのように処理します。  
受け取った関数側では、可変個引数をスライスとして扱います。  

可変個引数の呼び出しは以下のように記述しても同じように振舞います。  

```go
values := []string{"aaa", "bbb", "ccc"}
print("test", values...)
```
