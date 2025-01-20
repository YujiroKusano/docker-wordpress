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
# git環境設定手順
## gitのインストール手順
1. 以下から、gitのインストーラを取得。
>[Git for Windows](https://gitforwindows.org/)
2. Git-2.47.1.2-64-bit.exeを起動※デフォルトのままインストール。
## gitの基本操作
### ローカルリポジトリ操作
- リモートリポジトリからローカルリポジトリに落とす方法<br>
```git clone [リポジトリのURL]```
- リモートリポジトリの情報をもとにローカルリポジトリの情報を最新にする方法<br>
```git pull```
### ブランチ操作
- リモートブランチを元にローカルブランチを作成する方法<br>
```git branch [作成するローカルブランチ名] [remotes/origin/リモートブランチ名]```
- ローカルブランチの切り替え方法<br>
```git checkout [ローカルブランチ名]```
- リモートブランチをもとにローカルブランチを最新にする方法<br>
```git pull origin [ブランチ名]```
- リモートブランチを元にチェックアウト中の現在のローカルブランチのマージ方法
```git merge [リモートブランチ]```
- ローカルブランチをリモートブランチへ上げる方法<br>
```git push origin [ローカルブランチ名]```
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
