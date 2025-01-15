ResearchAndDevelopment
===============

社内研究開発案件に使用

## 開発環境
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
# git初期設定
- git
# Docker実行
```
$ cd [docker-compose.ymlのディレクトリパス]
$ docker-compose up -d # バックグラウンドで実行ワードプレス環境を起動
```
## データのバックアップ方法
```docker exec <db_container_name> mysqldump -uwordpress -pwordpress wordpress > backup.sql```
