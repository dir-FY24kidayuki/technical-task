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

psql上で以下のコマンドを使用することでデータベースの作成を行う。
```
CREATE DATABASE <データベース名>;
```
データベース名には、任意の名称が入る。

データベースが作成できたかは、
```
\l
```
で確認を行う。

## 他のデータベースに接続

上記でデータベースを作成した後、下記のコマンドで他のデータベースに接続することができる。
```
\c <データベース名>
```

## テーブルの作成
移行はsampleデータベース内でSQLコマンドを実行していく。
テーブルを作成するためには、以下のコマンドを使用する。
今回は例として、mybookテーブルを作成する。
```
CREATE TABLE mybook (id integer, name varchar(10));
```
作成できたかの確認を行うために、テーブル一覧を表示させる。
```
\z
```
テーブル定義を確認したいときは、以下のコマンドを実行する。
```
\d <テーブル名>
```

## テーブルへデータを追加

テーブルを作成した後、以下のコマンドでレコードを追加する。
```
INSERT INTO <テーブル名> (列名1, 列名2) VALUES (値1, 値2);
```
今回の例では、
```
INSERT INTO mybook (id, name) VALUES (1, 'からすのパンやさん');
```
> [!NOTE]
> ダブルクォーテーションではなく、シングルクォーテーションで文字列を囲うことに注意する。

## テーブルに追加したデータの取得

実際にレコードが追加できたかを確認する。
以下のようにSELECT文を使用して、データを取得する。
```
SELECT * FROM mybook;
```

## テーブル内にあるデータの削除

DELETE文を使用することでテーブルからレコードを削除することができる。

```
DELETE FROM <テーブル名>;
```
上記のようにコマンドを打つと、テーブルの中身全てが削除されてしまう。
レコードを指定する際は、WHERE句を一緒に用いる。
```
DELETE FROM mybook WHERE id=1;
```
これで、先ほど追加したレコードを削除することができた。

## 操作画面からログアウトできる

psql操作画面からログアウトするには、以下のコマンドを使用する。
```
\q
```
