# 配色設定


## 目次


- [カラーコード](#colorCode)

- [プロンプトの色設定](#promptColor)

- [ディレクトリの色設定](#dirColor)


## <a id="colorCode"></a> カラーコード

「文字種 (Attribute codes)」「文字色 (Text color codes)」「背景色 (Background color codes)」で構成される。

`文字種;文字色;背景色` で指定する (省略可)

コード | 文字種
---|---
00 | none (指定なし)
01 | bold (太文字)
04 | underscore (下線)
05 | blink (点滅)
07 | reverse
08 | concealed

コード | 文字色
---|---
30 | 黒
31 | 赤
32 | 緑
33 | 黄
34 | 青
35 | マゼンタ
36 | シアン
37 | 白

コード | 背景色
40 | 黒
41 | 赤
42 | 緑
43 | 黄
44 | 青
45 | マゼンタ
46 | シアン
47 | 白


## <a id="promptColor"></a> プロンプトの色設定

`\[\e[カラーコードm\]` のように指定し、`カラーコード` を省略するとデフォルト色になる


## <a id="dirColor"></a> ディレクトリの色設定

### 参考

- [WSLのWindowsのフォルダの色が見づらいのを直す](https://www.kwbtblog.com/entry/2019/04/27/023411)

### 変更手順

1. 現在の LS カラー設定ファイルを出力

  ```sh
  dircolors -p ~/.dircolors
  ```

1. LS カラー設定ファイルを編集

  以下は設定例

  ```sh
  # ディレクトリの色
  DIR 01;36 # directory

  # リンクの色
  LINK 01;32 # symbolic link. (If you set this to 'target' instead of a

  # other user の書き込み権限が付いたディレクトリの色
  OTHER_WRITABLE 01;36 # dir that is other-writable (o+w) and not sticky
  ```

1. LS_COLORS 設定

  `dircolors -b [設定ファイルパス]` で、LS_COLORS を設定するコードが出力されるので、以下を .bashrc に追記する

  ```sh
  eval $(dircolors -b ~/.bashrc)
  ```

1. 設定を適用

  ```sh
  source .bashrc
  ```

