# Apache module
apacheの拡張モジュールのON、OFFの方法  

# apache2 enable module
モジュールをenableする方法

    sudo a2enmod {モジュール名(php7.0)}

# apache2 disable module
モジュールをdisableする方法

    sudo a2dismod {モジュール名(php7.0)}

# apache2 restart
変更を加えた場合はシステムを再起動させる必要がある  

    sudo systemctl restart apache2.service

# help

## モジュールが機能しない
システムのバージョンアップなど、何かのタイミングで拡張モジュールが切断され、場合によってはphpなどのソースコードが解釈されずにそのまま表示されるなどの問題が発生することもある。  
そのようなときはenableしてあげる。  

