# postgresqlのパスワード設定
## ログインできる場合
psql等でログインしてからpassを設定する  
方法は2つ  

1.  

    =# \password
    [新しいpass]
    [もう一度pass]

2.  

    alter role [username] with password '新しいpass'

## passが不明でログインできない場合
pg_hba.confを設定して、pass無しでもログインできるように一時的に変更した後passを設定する  
pg_hba.confの場所を見つける  

    $ sudo find / -name pg_hba.conf
    -> /etc/postgresql/9.4/main/pg_hba.conf

pg_hba.confを編集する(ログイン方法をtrustに設定するからパスワードを指定せずにログインできるようになる。もちろん危険)  

    $ sudo vi /etc/postgresql/9.4/main/pg_hba.conf
    ---
    host  all     all    127.0.0.1/32    trust #こんな感じに変更

postgreを再起動  

    $ sudo /etc/init.d/postgresql reload

1章目と同じようにpassを設定  
pg_hba.confで設定した内容を元に戻す  
