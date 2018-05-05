# UTF-8
UTF8はここの文字を表すために、1バイトから4バイトのバイト数を使います。  
ASCII文字に対しては1バイトだけで表現されます。  
日本語は基本的に2バイトで表示されます。  


## １文字のビット数見分け
1文字を表すビット数が何かを見分ける方法があります。  

```
1Byte: 0xxxxxxx (ASCII)
2Byte: 110xxxxx 10xxxxxx (128未満は未使用)
3Byte: 1110xxxx 10xxxxxx 10xxxxxx (2048未満は未使用)
4Byte: 11110xxx 10xxxxxx 10xxxxxx 10xxxxxx (他の値は未使用)
```
