# PostgreSQL導入手順

## WSLのインストール

まずは、Windowsマシン上でWSL（Windows Subsystem for Linux）を使用できるように準備を行う。

> [!NOTE]
> 以下のコマンドを使用するには、Windows10 バージョン2004以上（ビルド19041以上）またはWindows11を実行している必要がある。

PowerShellまたはWindowsコマンドプロンプトを**管理者**モードで開き、以下のコマンドを入力し、マシンを再起動する。

```powershell:powershell
wsl --install
```
デフォルトでは、インストールされるLinuxディストリビューションはUbuntuになる。

## PostgreSQLのインストール

サーバのローカルパッケージインデックスを最新に更新する。
```
sudo apt update
```
追加のユーティリティと機能をいくつか追加する-contribパッケージとともにPostgresパッケージをインストールする。
```
sudo apt install postgresql postgresql-contrib
```

## PostgreSQLの起動

PostgreSQLを起動するには、以下のコマンドを実行する。
```
sudo service postgresql start
```
起動しているかの確認を行う。
```
sudo service postgresql status
```

## 操作画面へのログイン

デフォルトで作成されているpostgresユーザでpostgresにログインする。
```
sudo -u postgres psql
```

## データベースの作成

以下のコマンドでデータベースを作成できる。
```
CREATE DATABASE <データベース名>
```
データベース名に任意の名称を入力する。

## データベースに接続

コマンドを打って、データベースに接続することができる。

## テーブルの作成

データベース内にテーブルを作成できる。

## テーブルへデータを追加

テーブルを作成した後、データを追加できる。

## テーブルに追加したデータの取得

SELECT文を使用して、データを取得できる。

## テーブル内にあるデータの削除

DELETE文を使用して、データの削除ができる。

## 操作画面からログアウトできる

コマンドを打って、データベースからログアウトできる。

## 外部研修資料の振り返り

外部研修の振り返りをして、不明点をなくす。
