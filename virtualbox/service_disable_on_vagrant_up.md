# vagrantで再起動時にbashrcが正常に読み込まれない問題
正式な原因は分からないが、とりあえずの方法として起動後に以下のコマンドを実行する

    $ source ~/.bashrc

bashrcにrbenvなどの環境を書き込んでいた場合に、読み込まれないせいでコマンドとして認識してくれないことが多々ある
