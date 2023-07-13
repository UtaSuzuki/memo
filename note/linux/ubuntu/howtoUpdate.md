# WSL2 で Ubuntu をアップグレード

## 参考

[【WSL2】Ubuntu 20.04.4 LTS を 22.04 LTS へアップグレードした](https://zenn.dev/ryuu/articles/upgrade-ubuntu2204-wsl)

## 手順

### バックアップ

現行の環境を何かしらの形でバックアップしておく

### アップグレードのインストール準備

* ロケール変更
```sh
# 現在の環境で使用可能なロケールを確認
$ locale -a
# 日本語の言語パックをインストール
$ sudo apt install -y language-pack-ja
# インストールされたことを確認
$ locale -a
# 日本語ロケールを設定
$ sudo update-locale LANG=ja_JP.UTF8
# タイムゾーン変更
$ sudo dpkg-reconfigure tzdata
# 現在時刻確認
$ date
```
* 日本語対応
```sh
# コマンドのマニュアル表示を日本語化
$ sudo apt install -y manpages-ja manpages-ja-dev
# 確認
$ man apt
```

###  現行バージョンの確認

```sh
$ cat /etc/os-release
```

### パッケージの依存解決

```sh
$ sudo apt update && sudo apt upgrade -y
```

### ディストリビューションアップデートの確認

```sh
$ sudo apt dist-upgrade && sudo apt install -y update-manager-core
```

### release-upgrade の設定

/etc/update-manager/release-upgrades 内で、 `Prompt=lts` となっていることを確認

```sh
$ cat /etc/update-manager/release-upgrades

# なってなかったら編集
$ sudo vim /etc/update-manager/release-upgrades
```

### アップグレードの実行

```sh
$ sudo do-release-upgrade -d
```

途中で何度か `続行する[yN]  詳細 [d]` を聞かれるので回答する。

再起動してアップデート完了

### バージョン確認

```sh
$ cat /etc/os-release
```
