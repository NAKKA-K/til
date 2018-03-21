# apt server setting
ubuntuでaptしようと思ったら、404が返り正常に動作しない自体に陥った。 
そんな時はバージョンのサポートが切れている可能性が高い。  

以下のコマンドで確認する。   

    $ lsb_release -a

バージョンが表示されるので、[サポートページ][]でサポート期限を確認する。
サポートが切れているようであれば、以下のコマンドを実行する。

    $ sudo sed -i.bak -e "s%http://[^ ]\+%http://ftp.jaist.ac.jp/pub/Linux/ubuntu/%g" /etc/apt/sources.list

コマンドを実行したら、もう一度`apt update`して正常にできるか確認する。  

old-release.ubuntu.comにアクセスすることで解決した。  

[サポートページ]: http://www.ubuntulinux.jp/ubuntu

