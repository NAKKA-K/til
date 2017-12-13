# wordpress settings
centos7でのwordpress設定方法

# wordpressをダウンロード、展開
1. ネットからwordpressをtar.gz形式でダウンロード

    $ wget https://ja.wordpress.org/wordpress-4.9-ja.tar.gz

2. ダウンロードしたものを展開する

    $ tar -zxvf wordpress-4.9-ja.tar.gz

3. ドキュメントルートに移動させる
4. ドキュメントルートの権限をapacheに変更しておく

    $ chown -R apache /var/www/html/

# DBを用意する
mariaDBがインストールし初期設定を済ませているものとする

1. mariaDBにログイン

    $ mysql -u root -p

2. データベース作成

    > create database wp;

3. ユーザー作成

    > grant all on wp.* to wp@localhost identified by 'パスワード';

# サイトにアクセスして設定
1. サイトにアクセス(URL/wp)
2. 作成したDBの情報等々を設定すれば完了

