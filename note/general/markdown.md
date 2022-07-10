# Markdown の使い方

## 目次

- [レイアウト設定](#setting_layout)

- [見出し](#header)

- [段落](#paragraph)

- [表](#table)

- [コードブロック](#code_block)

- [フォントの装飾](#font_decoration)

- [リンク](#link)

- [箇条書き](#bullets)

- [水平線](#section_line)

- [画像の挿入](#image)

- [HTML 形式の定義リスト](#html)


## <a id="setting_layout"></a> レイアウト設定

マークダウンの先頭に、次のコマンドをセットすることで、レイアウトを設定できるらしい。。。？  
このレイアウトの設定ファイル `default` は `_layouts/default.html` に配置される。  
この設定によって画面のデザインを変更する事ができる。

~~~
---
layout: default
---
~~~


## <a id="header"></a> 見出し

```
# headding
## headding
### headding
#### headding
##### headding
###### headding
```

vvv 実行例 vvv

# hedding
## hedding
### hedding
#### hedding
##### hedding
###### hedding

^^^ ここまで ^^^


## <a id="paragraph"></a> 段落

```
AAA  BBB  CCC  
DDD  EEE  FFF

aaa<br>bbb<br>ccc<br>
ddd<br>eee<br>fff<br>
```

vvv 実行例 vvv

AAA  BBB  CCC  
DDD  EEE  FFF

aaa<br>bbb<br>ccc<br>
ddd<br>eee<br>fff<br>

^^^ ここまで ^^^

## <a id="table"></a> 表

```
Table | 1 | 2
:---:|:---:|:---:
Record1 | item1 | item2
Record2 | item1 | item2
Record3 | item1 | item2
Record4 | item1 | item2
Record5 | item1 | item2
```

vvv 実行例 vvv

Table | 1 | 2
:---:|:---:|:---:
Record1 | item1 | item2
Record2 | item1 | item2
Record3 | item1 | item2
Record4 | item1 | item2
Record5 | item1 | item2

^^^ ここまで ^^^

## <a id="code_block"></a> コードブロック

~~~
```sh
$ pwd
$ cd
$ ls
```
~~~

vvv 実行例 vvv

```sh
$ pwd
$ cd
$ ls
```

^^^ ここまで ^^^

## <a id="font_decoration"></a> テキストの装飾

```
**ボールド**
__ボールド__
_斜体(イタリック)_
~~取消し~~
`キーワード`
```

vvv 実行例 vvv

**ボールド**
__ボールド__
_斜体(イタリック)_
~~取消し~~
`キーワード`

^^^ ここまで ^^


## <a id="link"></a> リンク

```
[別ページ](<PATH>)
[ページ内見出し部](#<見出し名 または id>)
[外部サイト](<URL>)
```

vvv 実行例 vvv

- [別ページへのリンク](another-page)

- [この見出しへのリンク](#link)

- [外部サイトへのリンク](http://www.github.com/)

^^^ ここまで ^^^


## <a id="bullets"></a> 箇条書き

```
* 番号なし
  インデントすることで、メッセージ付加
* 番号なし
- 番号なし
  インデントすることで、メッセージ付加
- 番号なし
  - 入れ子にできる

1. 番号あり
1. 番号あり
  インデントすることで、メッセージ付加
1. 番号あり
  1. 番号あり
```

vvv 実行例 vvv

* 番号なし
  インデントすることで、メッセージ付加
* 番号なし
- 番号なし
  インデントすることで、メッセージ付加
- 番号なし
  - 入れ子にできる

1. 番号あり
1. 番号あり
  インデントすることで、メッセージ付加
1. 番号あり
  1. 番号あり

^^^ ここまで ^^^


## <a id="section_line"></a> 水平線

```
---
or
***
```

vvv 実行例 vvv

---
or
***

^^^ ここまで ^^^


## <a id="image"></a> 画像の挿入

```
![](https://assets-cdn.github.com/images/icons/emoji/octocat.png)
![](https://guides.github.com/activities/hello-world/branching.png)
```

vvv 実行例 vvv

![](https://assets-cdn.github.com/images/icons/emoji/octocat.png)
![](https://guides.github.com/activities/hello-world/branching.png)

^^^ ここまで ^^^


## <a id="html"></a> HTML 形式の定義リスト

```HTML
<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>
```

vvv 実行例 vvv

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

^^^ ここまで ^^^

