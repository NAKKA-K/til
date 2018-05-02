# SCP
scpコマンドの使用方法を説明します。  


## to vagrant
vagrantに対してsample.txtを転送する。  
転送先はvagrantユーザーの`~/`に転送する。  
```
$ vagrant ssh-config > ssh.config
$ scp -F ssh.config sample.txt vagrant@default:~/
```
