# memory
Go言語ではGCを実装しています。  
Goで領域がGCされるのは、その領域の値へ到達不可能になった時です。  
たとえば変数自体の生存期間の短いローカル変数のアドレスを、生存期間の長いグローバル変数に保存すると、常に到達可能状態ですのでGCからの領域回収を妨げることになります。  
これはメモリの効率が悪くなる行為です。  


## ヒープとスタック
通常、変数の宣言にはvarとnewがあります。  
簡単に考えるならvarで宣言すればスタック領域に、newで宣言すればヒープ領域となりそうですが、違います。  
この部分はコンパイラがローカル変数をヒープ上、あるいはスタック上のどちらに生成するか選択できます。  

```go
var global *int

func f(){
    var x int
    x = 1
    global = &x
}
fucn g(){
    y := new(int)
    *y = 1
}
```

以上の場合、x変数はヒープから割り当てられるべきです。  
ローカル変数として宣言されているが、globalから常に到達可能であるからです。  
このことをxはfからエスケープしていると言います。  
その逆に、yはgからエスケープしていません。  
そのためスタック上に生成しても安全です。  

それでも正しいコードを書くためにエスケープの概念を心配する必要はありません。  
しかし、エスケープする際には追加のメモリ割り当てを必要としますので、パフォーマンスを最適化する際にはエスケープの概念には気をつける必要があります。  
