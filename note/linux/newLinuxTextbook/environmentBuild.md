# 環境構築


## 目次

1. [ホームディレクトリ配下を日本語名から英語名に変更](#changeLangOnHome)


## <a id="changeLangOnHome"></a> ホームディレクトリ配下を日本語名から英語名に変更

```shell
LANG=C xdg-user-dirs-gtk-update
```

実行後に表示されるダイアログで  
`Don't ask me this again` にチェックを入れ、  
`Update names` をクリック

再起動後に自動表示されるダイアログでも  
`Don't ask me this again` にチェックを入れ、  
`Keep old folders` をクリック

