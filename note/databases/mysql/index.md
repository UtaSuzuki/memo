# MySQL

## 目次

- [インストール](#install)
- [DB 操作](#dbOperation)

## <a id="install"></a> インストール

### 参考

- [Ubuntu 20.04にMySQLをインストールする方法](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04-ja)

## <a id="dbOperation"></a> DB 操作

- [DB 作成](#makeDB)
- [TBL 作成/削除](#tbl)
- [主なデータ型](#dataType)
- [Warning 確認](#showWarn)

### <a id="makeDB"></a> DB 操作

```sql
CREATE DATABASE データベース名;
```

### <a id="tbl"></a> TBL 操作

- テーブル一覧
```sql
SHOW TABLES FROM データベース名;
```
- テーブル 作成
```sql
CREATE TABLE データベース名.テーブル名(
	フィールド名 データ型,
	[...]
);
```
- テーブル 削除
```sql
DROP TABLE データベース名.テーブル名;
```

### <a id="dataType"></a> 主なデータ型

型 | 表記
---|---
整数型 | INT, BIGINT, TINYINT
浮動小数点型 | DOUBLE, FLOAT
文字列型 | CHAR, VARCHAR
日付型 | DATE
時刻型 | DATETAME
テキスト型 | TEXT, LONGTEXT

### <a id="showWarn"></a> Warning 表示

```sql
SHOW warnings;
```
