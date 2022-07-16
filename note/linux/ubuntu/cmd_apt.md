# apt コマンドの使い方


## 目次

- [参考](#references)

- [リポジトリの更新 (apt update)](#update_repository)

- [更新の実行](#perform_update)

- [不要なパッケージを削除](#delete_unnecessary_packages)


## <a id="references"></a> 参考

- [有限工房 | Ubuntuのaptコマンドの使い方](https://ygkb.jp/5393)


## <a id="update_repository"></a> リポジトリの更新 (apt update)

ローカルリポジトリ (バージョン管理 DB) を最新状態に更新

```sh
$ sudo apt update
```


## <a id="excuse_update"></a> 更新の実行 (apt upgrade)

ローカルリポジトリの内容を元に実際の更新処理を実行

```sh
$ sudo apt upgrade
```


## <a id="delete_unnecessary_packages"></a> 不要なパッケージを削除

不要になったパッケージを自動的に削除

```sh
$ sudo apt autoremove
```

