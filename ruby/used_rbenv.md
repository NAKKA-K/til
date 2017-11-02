# rbenv,ruby-buildを使う
## rubyのインストール
rbenvがインストールされている場合、`rbenv install -v`でインストールできるバージョンを確認  
`rbenv install 2.4.2`で指定したバージョンをインストール  

## rubyのバージョン表示
`rbenv versions`でインストール済みRubyのバージョンリストが見れる  
`*`の表示されているバージョンは、カレントディレクトリで有効なRubyバージョン  

## rubyのバージョン選択
`rbenv global 2.4.2`で環境全体でRubyのバージョンを指定できる  
`rbenv local 2.4.2`でディレクトリ固有のRubyバージョンを指定できる  

## rbenv,ruby-buildの更新
### Linux

    $ cd ~/.rbenv
    $ git pull
    $ cd ~/.rbenv/plugins/ruby-build
    $ git pull

### MacOSX

    $ brew update
    $ brew upgrade rbenv ruby-build
