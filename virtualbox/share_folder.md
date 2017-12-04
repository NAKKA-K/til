# virtualbox share folder
VirtualBoxで共有フォルダを使用する場合、デフォルトではファイルの権限がないと怒られる。  
そのため以下の設定が必要

    $ sudo gpasswd -a [ユーザ名] vboxsf

その後、ログオフ、ログイン
