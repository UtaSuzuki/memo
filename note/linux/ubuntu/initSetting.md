# 初期設定


## 目次

- [参考](#references)

- [リポジトリ変更](#changeRepository)

- [更新](#update)

- [日本語環境の設定](#setJapaneseEnv)

- [タイムゾーンの設定](#setTimeZone)

- [man コマンドの設定](#setMan)


## <a id="references"></a> 参考

- [初心者のためのWSL( 1 ) ~初期設定,CUI設定編~](https://qiita.com/yoshige/items/dbc85b048fba51e597ee)


## <a id="changeRepository"></a> リポジトリ変更

```sh
# sources.list の存在確認
$ ls /etc/apt/sources.list
$ sudo sed -i.bak -e "s|http://archive.ubuntu.com|http://jp.archive.ubuntu.com|g" /etc/apt/sources.list
# sources.list と sources.list.bak の存在確認
$ ls /etc/apt/sources.list*
```


## <a id="update"></a> 更新

```sh
$ sudo apt update -y
$ sudo apt upgrade -yV
$ sudo apt dist-upgrade -yV
$ sudo apt autoremove -yV
$ sudo apt autoclean
```


## <a id="setJapaneseEnv"></a> 日本語環境の設定

```sh
$ sudo apt install -y language-pack-ja
$ sudo update-locale LANG=ja_JP.UTF-8
```

再起動するために、Ubuntu で

```sh
$ exit
```

PowerShell で

```
> wsl -l -v
> wsl -t <DIST-NAME>
> wsl -l -v
```

スタートメニューから起動

日本語環境になってるか確認

```sh
$ echo $LANG
ja_JP.UTF-8
```


## <a id="setTimeZone"></a> タイムゾーンの設定

```sh
$ sudo dpkg-reconfigure tzdata
```

「パッケージの設定」画面が表示されるので、[アジア] -> [東京] を選択

タイムゾーンの確認

```sh
$ date
YYYY年  M月  D日 ？曜日 hh:mm:ss JST
```


## <a id="setMan"></a> man コマンドの設定

日本語マニュアルのインストール

```sh
$ sudo apt install -y manpages-ja manpages-ja-dev
```

確認

```sh
$ man ls
```

