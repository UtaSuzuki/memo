# apt コマンドの使い方


## 目次

- [参考](#references)

- [コマンド一覧](#cmd_list)

- [コマンドログ](#cmd_log)


## <a id="references"></a> 参考

- [有限工房 | Ubuntuのaptコマンドの使い方](https://ygkb.jp/5393)

- [Qiita: @SUZUKI_Masaya さん | aptコマンドチートシート](https://qiita.com/SUZUKI_Masaya/items/1fd9489e631c78e5b007)


## <a id="cmd_list"></a> コマンド一覧

コマンド | 説明
---|---
`sudo apt update` | ローカルリポジトリ (バージョン管理 DB) を最新状態に更新
`sudo apt upgrade` | ローカルリポジトリの内容を元に実際の更新処理を実行<br>(通常のパッケージ更新時に使用)
`sudo apt autoremove` | 不要になったパッケージを自動的に削除<br>(apt 実行時に表示されたときに実行)
`sudo apt autoclean` | キャッシュされているが、インストールはされていない deb ファイルを削除
`sudo apt full-upgrade` | ローカルリポジトリの内容を元に実際の更新処理を実行<br>(保留されているパッケージの更新時に使用)
`sudo apt install [パッケージ | deb ファイル]` | パッケージや deb ファイルをインストール
`sudo apt remove [パッケージ]` | パッケージを削除
`sudo apt remove --purge [パッケージ]` | パッケージを完全削除
`sudo apt show [パッケージ]` | パッケージの詳細情報を表示
`sudo apt list [パッケージ]` | パッケージを検索 (完全一致)
`sudo apt search [パッケージ]` | パッケージを検索 (部分一致)
`sudo apt list --installed | grep [パッケージ]` | パッケージを検索 (部分一致)
`sudo apt list --installed` | インストール済のパッケージ一覧を表示


## <a id="cmd_log"></a> コマンドログ

場所 : `/var/log/apt/history.log`

