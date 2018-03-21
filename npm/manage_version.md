# manage version of npm and nodejs
通常のaptでインストールするnpmなどは、バージョンが古かったり、管理が面倒  
そのためrbenvやpyenvの様なバージョン管理ソフトを使用する  


- npmコマンドを使うために一旦インストール  

```bash
$ sudo apt install -y nodejs npm
```


- 本命の`n package`をインストール  

```bash
$ sudo npm cache clean
$ sudo npm install n -g
```


- `n package`を使って`node`をインストール  

```bash
$ sudo n stable
$ sudo ln -sf /usr/local/bin/node /usr/bin/node
```


- 最新バージョンインストールの確認  

```bash
$ node -v
```


- aptで入れたnodejsとnpmを削除

```bash
$ sudo apt purge -y nodejs npm
```


## 別バージョンを管理する方法

```bash
$ sudo n 5.2.0
```

