# Virtualboxでは共有フォルダでシンボリックリンクが使えない
Virtualboxはセキュリティ上の理由から、共有フォルダにシンボリックリンクを許可していない  

## 問題点
1. WindowsのPath長制限(260文字)に引っかかっている
2. Virtualboxではセキュリティの関係、共有フォルダにsymlinkを張れない
3. Windowsがsymlinkをサポートしていない

## 解決策
### 単純な解決
**共有フォルダ以外で作業をする！**


### 共通の解決策
symlinkを張らないようにオプションを設定する  
`npm install`であれば`--no-bin-links`フラグを指定することによって、symlinkを生成しない

```
$ npm install --no-bin-links
```

### ホストがWindows以外の解決策
シンボリックリンクを有効にするには、`Vagrantfile`の**config.vm.provider**ブロックに次の行を追加する必要がある  

```
config.vm.provider "virtualbox" do |v|
    v.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]
end
```

### ホストがWindowsの場合
ホストOSがWindowsの場合、共有フォルダにsymlinkを張ることはできない  
何故ならWindowsがsymlinkをサポートしていないためである
そしてpath長が260文字以内であるため、それを超えるpathはエラーになる  
この場合の解決策としては共有フォルダ以外で作業をすること以外に解決策はないものと考える  

---
[参考][]

[参考]: https://github.com/npm/npm/issues/7308
