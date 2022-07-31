# Git


## 目次

- [参考](#references)

- [初期設定](#initSetting)

- [GitHub と連携](#alignmentGitHub)

- [ローカルリポジトリを作成](#makeLocalRepo)

- [編集の流れ](#edittingFlow)

- [【参考書】わかばちゃんと学ぶ Git 使い方入門](refBook_Wakaba.md)


## <a id="references"></a> 参考

- [Gitをインストールしたら真っ先にやっておくべき初期設定](https://qiita.com/wnoguchi/items/f7358a227dfe2640cce3)


## <a id="initSetting"></a> 初期設定

```sh
# ユーザ情報の設定
$ git config --global user.name "ユーザ名"
$ git config --global user.email "メールアドレス"

# エディタを Vim に設定
$ git config --global core.editor 'vim -c "set fenc=utf-8"'

# .gitignore を定義 (このファイルに書かれたものは Git 管理外とする)
$ git config --global core.excludesfile ~/.gitignore

# ファイル名の大文字小文字を区別
$ git config --global core.ignorecase false

# Mac-Linux 環境間での日本語ファイル名文字化け対策
$ git config --global core.precomposeunicode  true

# git status した際の日本語ファイル名文字化け対策
$ git config --global core.quotepath  false

# ページャの設定
$ git config --global core.pager "less --no-init -iRMXF"

# 色付け
$ git config --global color.ui auto

# push 方式を指定 (明示しないと警告される)
$ git config --global push.default simple

# git 認証情報を ~/.git-credentials に保存
$ git config --global credential.helper "store --file ~/.git-credentials"

# git difftool でファイル差分を見る際に使用するツール
$ git config --global diff.tool vimdiff

# git difftool を実行した時の Y/n の確認を表示しない
$ git config --global difftool.prompt false

# コンフリクトしたファイルを git mergetool でマージする際に使用するツール
$ git config --global merge.tool vimdiff

# コンフリクトしたファイルに対して git mergetool を実行した時の Y/n の確認を表示しない
$ git config --global mergetool.prompt false

# エイリアス設定
$ git config --global alias.graph "log --graph --all --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative"
$ git config --global alias.br branch
$ git config --global alias.co checkout
$ git config --global alias.st status
$ git config --global alias.di diff
$ git config --global alias.ad add
$ git config --global alias.cm commit
$ git config --global alias.ps push
```


### git-completion.bash

Git コマンドの補完スクリプト ([TAB] で補完できる)

```sh
$ wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash -O ~/.git-completion.bash
$ chmod a+x ~/.git-completion.bash
$ echo "source ~/.git-completion.bash" >> ~/.bashrc
$ source ~/.bashrc
```

### git-prompt.sh

プロンプトに各種追加情報を表示可能にするスクリプト

```sh
$ wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh -O ~/.git-prompt.sh
$ chmod a+x ~/.git-prompt.sh
$ echo "source ~/.git-prompt.sh" >> ~/.bashrc
# ~/.bashrc 内の PS1 変数に __git_ps1 を追加
$ vim ~/.bashrc
$ source ~/.bashrc
```

### オプション (1 or null)

- GIT_PS1_SHOWUPSTREAM

  \> : 現在のブランチが upstream より進んでいるとき  
  < : 現在のブランチが upstream より遅れているとき  
  <> : 現在のブランチが upstream より遅れてるけど独自の変更もあるとき

- GIT_PS1_SHOWUNTRACKEDFILES

  % : 未ステージングの新規ファイルがあるとき (untracked)

- GIT_PS1_SHOWSTASHSTATE

  $ : stash になにか入っているとき (stashed)

- GIT_PS1_SHOWDIRTYSTATE

  \* : 未ステージングのファイルがあったとき (unstaged)  
  \+ : ステージング済みで未コミットのファイルがあったとき (staged)


## <a id="alignmentGitHub"></a> GitHub と連携

自分のアカウントページから `New` ボタンでリポジトリ作成

以下を設定

- Repository name
- Description
- Public / Private
- Initialize this repository with a REDME (自分で用意するならチェック OFF)
- Add .gitignore (自分で用意するなら None で OK)
- Add a license (None で OK)

リポジトリページでリポジトリ URL を控えておくと良い

また、`push` 時は、アクセストークンが必要。
（取得済み。忘れたときは、更新可能）

ローカルリポジトリにリモートリポジトリを登録

```sh
# リモートリポジトリの URL をローカルリポジトリに登録 (origin として)
$ git remote add origin [リポジトリ URL]

# 確認
$ git remote -v
origin [リポジトリ URL] (fetch)
origin [リポジトリ URL] (push)
```


## <a id="makeLocalRepo"></a> ローカルリポジトリを作成

```sh
# カレントディレクトリを Git 管理対象に設定
$ git init

# 確認
$ ls -a .git

# 最初のコミット
$ git commit --allow-empty -m "[NEW] Make local repository"
$ git log

# プッシュ
$ git push origin master
```


## <a id="edittingFlow"></a> 編集の流れ

1. ブランチ作成

  命名規則 : `[タグ]_[概要]`

  タグ | 説明
  ---|---
  release | 新規開発など
  feature | 機能変更など
  hotfix | バグ修正など

  ```sh
  # ブランチ作成 & チェックアウト
  $ git checkout -b "ブランチ名"

  # 確認
  $ git branch
  ```

1. リモートの更新を適用

  ```sh
  # fetch と merger を個別に実行
  #$ git fetch origin master
  #$ git merge origin/master

  # 一括で適用
  $ git pull
  ```

1. ファイル編集

  Vim などでファイル編集

1. リモートリポジトリに適用

  コミットメッセージ規則 : `[タグ]_[概要]`

  タグ | 説明
  ---|---
  new | 新規
  mod | 変更 (機能の変更や追加)
  fix | 修正 (バグなどの機能追加を含まないもの)

  ```sh
  # ローカルリポジトリの状態確認
  $ git status

  # ステージング (すべてをステージングの
  ## 任意の更新ファイルをステージング
  $ git add [更新ファイル]
  ## すべての更新ファイルをステージング
  $ git add .

  # ステージング確認
  $ git status

  # コミット
  $ git commit -m "コミットメッセージ"

  # コミット確認
  $ git status
  $ git log --oneline -10

  # プッシュ
  $ git push origin [ブランチ名]
  ```

