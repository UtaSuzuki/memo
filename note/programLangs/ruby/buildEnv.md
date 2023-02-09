# Ruby の開発環境構築 (Rails まで)

## 目次

## 初期状態

```sh
[yuta@U-DESKTOP ~] 2023/02/09-22:20:52
$ ruby -v

コマンド 'ruby' が見つかりません。次の方法でインストールできます:

sudo apt install ruby


[yuta@U-DESKTOP ~] 2023/02/09-22:21:18
$ gem -v

コマンド 'gem' が見つかりません。次の方法でインストールできます:

sudo apt install ruby


[yuta@U-DESKTOP ~] 2023/02/09-22:21:20
$ gcc -v

コマンド 'gcc' が見つかりません。次の方法でインストールできます:

sudo apt install gcc


[yuta@U-DESKTOP ~] 2023/02/09-22:21:23
$ g++ -v

コマンド 'g++' が見つかりません。次の方法でインストールできます:

sudo apt install g++


[yuta@U-DESKTOP ~] 2023/02/09-22:21:26
$ make -v

コマンド 'make' が見つかりません。次の方法でインストールできます:

sudo apt install make        # version 4.2.1-1.2, or
sudo apt install make-guile  # version 4.2.1-1.2
```

## rbenv をインストール

### 参考

- [rbenv を使った ruby インストール方法 (Mac・linux)](https://valed.press/programming-learning/how-to-install-ruby-with-rbenv/)
- [rbenv を使っているなら rbenv-gem-rehash を使おう](https://qiita.com/riocampos/items/f0fe7217972b312c4f3a)

### 作業

`rbenv` `ruby-build` `rbenv-gem-rehash` をインストール
- rbenv: ruby のバージョン管理を行うためのツール
- ruby-build: rbenv のプラグインの 1 つ。ruby をインストールするために必要。
- rbenv-gem-rehash: gem のインストール/アンインストールごとに自動で `ruby rehash` してくれる

```sh
$ git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
$ git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
$ git clone https://github.com/sstephenson/rbenv-gem-rehash.git ~/.rbenv/plugins/rbenv-gem-rehash
```

`.bashrc` に追記して適用

```sh
# PATH を追加
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc

# Ubuntu 起動時に rbenv を自動で起動
$ echo 'eval "$(rbenv init -)"' >> ~/.bashrc

#　適用
$ source ~/.bashrc
```

必要なパッケージをインストール

```sh
$ sudo apt install gcc g++ build-essential libssl-dev libreadline-dev zlib1g-dev libyaml-dev
```

`ruby` をインストール

```sh
# インストール可能なバージョンを確認
$ rbenv install --list

# 任意のバージョンをインストール
$ rbenv install x.x.x

# グローバルバージョンを指定
$ rbenv global x.x.x

# 現在のバージョン確認
$ ruby -v
```

`bundler` のインストール

```sh
# インストール
$ gem install bundler

# 確認
$ bundler -v
```

`Rails` のインストール

```sh
# インストールできる安定バージョンを全て表示
$ gem list rails -rea

# バージョン指定なしのときにインストールされる最新安定版を確認
$ gem list rails -re

# 任意のバージョンをインストール
$ gem install rails -v '~> x.x.x'

# 確認
$ rails -v
```

※ バージョン指定方法について
- `指定なし` : 常に最新版を利用
- `'1.0.0'` : 1.0.0 で利用可能
- `'>= 1.0.0'` : 1.0.0 以上で利用可能
- `'>= 1.0.0, < 2.0.0'` : 1.x.x で利用可能 (1.0.0 以上、2.0.0 未満)
- `'~> 1.0.0'` : 1.0.x で利用可能 (1.0.0 以上、1.1.0 未満)

