# djangoでdbの接続設定
## postgresqlを使用する場合
### 依存ライブラリのインストール
まずはPythonからpostgreを使用するためのライブラリ等をインストールする

    $ sudo apt-get install libpq-dev python-psycopg2

次はpythonの開発環境が整っている状態でインストールする

    $ pip install psycopg2

### postgreに新しいユーザー、パスワード、データベースの作成
postgreにスーパーユーザーでログインして作成する

    $ su - postgres
    $ psql
    =# CREATE ROLE [新しいuser] WITH PASSWORD '新しいpass'; (ユーザ作成)
    =# CREATE DATABASE [新しいdb] OWNER [新しいuser] ENCODING 'UTF8'; (データベース作成)

### djangoの設定ファイルにdbの設定を書き込む
djangoのプロジェクト内のsettings.pyを編集

    $ vi settings.py
    ---
    DATABASE = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql_psycopg2', # postgreを使用する場合
            'NAME': 'dw2018db', # アプリケーションで使用するdb
            'USER': 'develop17', # postgreのユーザー
            'PASSWORD' : 'develop17', # 一つ上のユーザーのパスワード
            'HOST' : '127.0.0.1',
            'PORT' : 5432, # postgresqlのデフォルトport
        }
    }

上記の設定を反映させるためにマイグレーションを実行する

    $ python manage.py migrate


