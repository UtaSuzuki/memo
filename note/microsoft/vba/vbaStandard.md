# VBA スタンダード対策


## 目次

- [参考](#references)

- [プロシジャ](#procedure)

- [変数](#variables)

- [ステートメント](#statement)

- [ファイル操作](#fileOperation)

- [ワークシート関数](#worksheetFunction)

- [セル検索とオートフィルタ](#findAndAutofilter)

- [ソート](#sort)

- [テーブル操作](#tableOperation)

- [エラー対策](#errorHandling)

- [デバッグ](#debug)


## <a id="references"></a> 参考

- [VBA エキスパート 公式テキスト] Excel VBA スタンダード

	著者 : 田中 亨  
	発行 : 株式会社オデッセイ コミュニケーションズ


## <a id="procedure"></a> プロシジャ

VBA のセクション領域

```
┌─ モジュール ──────────
│
│ ' コメント
│
│ ┌─ 宣言セクション ──────
│ │
│ │ モジュールレベル変数 を定義する場所
│ │
│ └───────────────
│
│ ┌─ プロシジャ定義セクション ─
│ │
│ │ Sub プロシジャ
│ │
│ │ Function プロシジャ
│ │
│ └───────────────
│
└─────────────────
```

Sub プロシジャ

```
' 返り値がないプロシジャ

' === 宣言 ===
Sub プロシジャ名(仮引数)
    処理
End Sub

' === 呼び出し ===
Call プロシジャ名(実引数)
```

Function プロシジャ

```
' 返り値があるプロシジャ

' === 宣言 ===
Function プロシジャ名(仮引数)
    処理
    プロシジャ名 = 返り値
End Function

' === 呼び出し (例) ===
Range("A1") = プロシジャ名(実引数)
```

仮引数の宣言

```
' 構文
仮引数名 As 型名

' 例
A As Long
```

プロシジャの強制終了

```
' Sub プロシジャの例

Sub プロシジャ名(仮引数)
    処理
    If 条件 Then
        Exit Sub
    End If
    処理
End Sub

' Function プロシジャの例

Function プロシジャ名(仮引数)
    処理
    If 条件 Then
        Exit Function
    End If
    処理
    プロシジャ名 = 返り値
End Function
```

値渡しと参照渡し



## <a id="variables"></a> 変数

型一覧

表記 | 型 |備考
---|---|---
String | 文字列 |
Long |

## <a id="statement"></a> ステートメント

## <a id="fileOperation"></a> ファイル操作

## <a id="worksheetFunction"></a> ワークシート関数

## <a id="findAndAutofilter"></a> セル検索とオートフィルタ

## <a id="sort"></a> ソート

## <a id="tableOperation"></a> テーブル操作

## <a id="errorHandling"></a> エラー対策

## <a id="debug"></a> デバッグ

