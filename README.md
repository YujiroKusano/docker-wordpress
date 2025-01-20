ResearchAndDevelopment
===============
社内研究開発案件に使用
# 開発環境
## 環境情報
- Docker
```
$ docker -v
Docker version 27.0.3, build 7d4bcd8
$ docker-compose -v
Docker Compose version v2.28.1-desktop.1
```
- WordPress
```
version:    6.7.1
plugin:     -
theme:      -
```
# Docker環境設定手順
## Dockerインストール手順
1. 以下から、dockerのインストーラを取得。※「Download for Windows - AMD64」を選択
>[Get Started with Docker](https://www.docker.com/get-started/)
2. Docker Desktop Installer.exeを起動。※デフォルトのままインストール。
## Docker初期設定手順
```
$ export DOCKER_CLI_DISABLE_CREDENTIAL_HELPER=1
$ docker login -u [ユーザ名] #その後パスワード入力を求められる
```
## Docker実行手順
```
$ cd [docker-compose.ymlのディレクトリパス]
$ docker-compose up -d # バックグラウンドで実行WordPress環境を起動
```
## Docker停止手順
```
$ docker-compose down
```
## データのバックアップ方法
```docker exec <db_container_name> mysqldump -uwordpress -pwordpress wordpress > db_backup.sql```

## 起動方法
1.対象のディレクトリへ移動<br>
  ```cd [docker-compose.ymlと同列のパス]```<br>
2. Dockerの起動<br>
  ```docker-compose up -d```<br>
3. 共有データ（SQL）を```docker-compose.yml```と同列に配置※共有データの場所は上長に確認<br>
4.  共通DBの読み込み<br>
  ```docker exec -i researchanddevelopment-db-1 mysql -uwordpress -pwordpress wordpress < db_backup.sql```<br>
