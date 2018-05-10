# Go lang method is defer
Go言語のdefer文は特殊な文法です  
呼び出し元の関数の終了後、deferで渡された引数が実行されます。
deferの呼び出しはスタックに格納され、呼び出し元関数実行後popしながら実行していきます。

deferに渡された引数が、複数の関数実行によって成り立っている場合、一番親の関数以外の関数はその時点で実行されます。  

```go
func bigSlowOperation() {
	defer trace("bigSlowOperation")()()
	time.Sleep(2 * time.Second)
}

func trace(msg string) func() func() {
	log.Printf("enter %s", msg)
	return end
}
func end() func() {
	log.Printf("end")
	return func() {
		log.Printf("extend")
	}
}

//=> enter bigSlowOperation
//=> end
// (sleepで待たされる)
//=> extend
```

## 使用例
- ファイル、リソースのClose
- デバックのために、自関数の戻り値を表示する
- デバックのために、無名関数を返す関数を呼び出すことによって、内部で時間の計測を行わせる
