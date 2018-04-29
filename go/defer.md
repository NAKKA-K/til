# Go lang method is defer
Go言語のdefer文は特殊な文法です  
呼び出し元の関数の終了後、deferで渡された引数が実行されます。
deferの呼び出しはスタックに格納され、呼び出し元関数実行後popしながら実行していきます。
