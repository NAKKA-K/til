# string
Go言語でのstringについて説明します。  

stringの代入は基本的にコピーです。  
コストはそれなりにかかりますが、ループで繰り返さない限り十分低コストです。  
コピーで実装されている理由としては、元の文字列に対しての影響を限りなくなくすためです。  
もし参照が渡されている場合、片方の文字列を変更した場合に大きな影響が出てしますためです。  

たとえば文字列同士の結合をしつつ再代入するループ処理を組んだ場合、文字列連結の度に新しく文字列をコピーするのでコストが高くなってしまいます。  
文字列の加工を何度もする場合は、`bytes.Buffer`を使用してください。  
BufferのWrite系関数で書き込むか、Fprint系の関数でBufferへのアドレスへ書き込むなどの方法があります。  
