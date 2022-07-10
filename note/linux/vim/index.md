# Vim


## 目次

- [文字コード変更](#changeCharSet)


## <a id="changeCharSet"></a> 文字コード

### 参考

- [Vimで文字コードを指定する](https://qiita.com/bezeklik/items/2c9925f9c07762559471https://qiita.com/bezeklik/items/2c9925f9c07762559471)

### 確認

```vim
# Vim のエンコード
:se enc?

# ファイルのエンコード
:se fenc?
```

### 開き直す

```vim
# Long command
:edit ++encoding=[char set]

# Short command
:e ++enc=[char set]
```

### 保存

```vim
# Long command
:set fileencoding=[char set]

# short comannd
:se fenc=[char set]
```
