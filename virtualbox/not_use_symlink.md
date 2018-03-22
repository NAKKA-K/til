# Virtualboxではシンボリックリンクが使えない
Virtualboxはセキュリティ上の理由から、共有フォルダにシンボリックリンクを許可していない  
シンボリックリンクを有効にするには、`Vagrantfile`の**config.vm.provider**ブロックに次の行を追加する必要がある  

```
config.vm.provider "virtualbox" do |v|
    v.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]
end
```

[参考:][]

[参考:]: https://github.com/npm/npm/issues/7308
