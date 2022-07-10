# Git


## 目次

- [参考](#references)

- [初期設定](#initSetting)

- [GitHub と連携](#alignmentGitHub)

- [ローカルリポジトリを作成](#makeLocalRepo)

- [編集の流れ](#edittingFlow)


## <a id="references"></a> 参考

- [Gitをインストールしたら真っ先にやっておくべき初期設定](https://qiita.com/wnoguchi/items/f7358a227dfe2640cce3)


## <a id="initSetting"></a> 初期設定

```sh
# ユーザ情報の設定
git config --global user.name "ユーザ名"
git config --global user.email "メールアドレス"

# エディタを Vim に設定
git config --global core.editor 'vim -c "set fenc=utf-8"'

# git diff に色付け
git config --global color.diff auto
git config --global color.status auto
git config --global color.branch auto

# push 方式を指定 (明示しないと警告される)
git config --global push.default simple

# git 認証情報を自動保存
git config --global credential.helper store
```


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
git remote add origin [リポジトリ URL]

# 確認
git remote -v
origin [リポジトリ URL] (fetch)
origin [リポジトリ URL] (push)
```


## <a id="makeLocalRepo"></a> ローカルリポジトリを作成

```sh
# カレントディレクトリを Git 管理対象に設定
git init

# 確認
ls -a .git

# 最初のコミット
git commit --allow-empty -m "[NEW] Make local repository"
git log

# プッシュ
git push origin master
```


## <a id="edittingFlow"></a> 編集の流れ

1. ブランチ作成 (編集の最初だけ)

	命名規則 : `[タグ]_[概要]`

	タグ | 説明
	---|---
	release | 新規開発など
	feature | 機能変更など
	hotfix | バグ修正など

	```sh
	# ブランチ作成 & チェックアウト
	git checkout -b "ブランチ名"

	# 確認
	git branch
	```

1. リモートの更新を適用

	```sh
	# fetch と merger を個別に実行
	#git fetch origin master
	#git merge origin/master

	# 一括で適用
	git pull
	```

1. ファイル編集

	Vim などでファイル編集

1. リモートリポジトリに適用

	コミットメッセージ規則 : `[タグ]_[概要]`

	タグ | 説明
	---|---
	NEW | 新規
	MOD | 変更 (機能の変更や追加)
	FIX | 修正 (バグなどの機能追加を含まないもの)

	```sh
	# ローカルリポジトリの状態確認
	git status

	# ステージング (すべてをステージングの
	## 任意の更新ファイルをステージング
	git add [更新ファイル]
	## すべての更新ファイルをステージング
	git add .

	# ステージング確認
	git status

	# コミット
	git commit -m "コミットメッセージ"

	# コミット確認
	git status
	git log --oneline -10

	# プッシュ
	git push origin [ブランチ名]
	```

