# upload django to heroku

# アカウント登録
herokuのsignupページで、アカウント作成

# herokuにログイン

    $ heroku login

# herokuアプリを作成
herokuでプロジェクトを作成する。プロジェクト名は省略すれば、自動で設定される。

    $ heroku create [project_name]

---

# プロジェクトに追加するファイル、設定

## runtime.txt
稼働させるプログラムのバージョンを記述する

    $ echo "`python -v`" > runtime.txt

## Procfile
herokuで稼働させる方法を記述。gunicornはrunserverの本番環境版のようなもの。

    $ echo "web: gunicorn [app_name].wsgi --log-file" > Procfile

runserverもできる。

    $ echo "web: python manage.py runserver 0.0.0.0:${PORT}" > Procfile

## [project_name]/settings.py
ファイルの最後に以下の設定を追記。

```[project_name]/settings.py
import dj_database_url
DATABASS['default'] = dj_database_url.config()

SECURE_PROXY_SSL_HEADER = ('HTTP_X_FORWARDED_PROTO', 'https')

ALLOWED_HOST = ['*']

STATIC_ROOT = 'static'

DEBUG = False

try:
  from .local_settings import *
except ImportError:
  pass
```

## [project_name]/local_settings.py
ローカル環境用の設定を追記。settings.pyを上書きする形で設定される。  
ファイルの最後に以下の設定を追記。  

```[project_name]/local_settings.py
import os
BASE_DIR = os.path.dirname(os.path.dirname(__file__))

DATABASES = {
  'default': {
    'ENGINE': 'django.db.backends.sqlite3',
    'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
  }
}

DEBUG = True
```

## [project_name]/wsgi.py
ファイルの最後に以下の設定を追記。  

```[project_name]/wsgi.py
from whitenoise.django import DjangoWhiteNoise
application = DjangoWhiteNoise(application)
```

## heroku環境変数の設定
この設定をしないと、herokuにpushしたときに怒られる。

    $ heroku config:set DISABLE_COLLECTSTATIC=1

## herokuへアップ
gitを使用してアップする。  
アップ先URLをremoteに登録する。  

    $ git remote add heroku https://git.heroku.com/[project_name].git
    $ git push heroku master

テスト用ブランチの内容を公開したい場合は以下のようにする。

    $ git push heroku [test_branch]:master

## herokuでDBの反映

    $ heroku run python manage.py migrate

## heroku で管理サイト用のアカウントを作成

    $ heroku run python manage.py createsuperuser
    
## herokuにアップしたプロジェクトを起動
これをすることによって、ブラウザからアクセスできるようになる。

    $ heroku open

