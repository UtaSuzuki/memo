# VBA スタンダード対策


## 目次

- [参考](#references)

- [主な関数](#functions)

- [主なプロパティ](#properties)

- [主なメソッド](#methods)

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


## <a id="functions"></a> 主な関数

- Split

	文字列を任意の区切り文字で分割し、配列として返す

	```
	Split("A-B-C", "-")    ' > [A, B, C]
	```

- UBound

	配列の最大インデックスを返す

	```
	Dim A(3) As String
	MsgBox UBound(A)      ' > 3
	```


## <a id="properties"></a> 主なプロパティ

- Name

	各種オブジェクトの名前

	```
	Workbook.Name
	Worksheet.Name
	```

- ColorIndex

	文字色を 1 ～ 56 のインデックスから指定

	```
	RangeObj.Font.ColorIndex(番号)
	```




## <a id="methods"></a> 主なメソッド

- ワークシート追加

	`Worksheets` コレクションの `Add` メソッドを使用

	```
	WorksheetsColllection.Add
	```

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

```vba
' 返り値がないプロシジャ

' === 宣言 ===
Sub プロシジャ名(仮引数)
    処理
End Sub

' === 呼び出し ===
Call プロシジャ名(実引数)
```

Function プロシジャ

```vba
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

```vba
' 構文
仮引数名 As 型名

' 例
A As Long
```

プロシジャの強制終了

```vba
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

```vba
Sub Sample()
    Dim X As Long
    X = 100

    Call ValSample(X)
    MsgBox X           ' > 100 (変化なし)

    Call RefSample(X)
    MsgBox X           ' > 200 (変化あり)
End Sub

' 値渡し: ByVal
' 仮引数には実引数の「値」が渡される
Sub ValSample(ByVal A As Long)
    ' 仮引数を変更しても、実引数に影響なし
    A = A * 2
End Sub

' 参照渡し: ByRef (デフォルト)
' 仮引数には実引数の「アドレス」が渡される
Sub RefSample(ByRef A As Long)
    ' 仮引数を変更すると、実引数も変更される
    A = A * 2
End Sub
```

## <a id="variables"></a> 変数

- データ型一覧

	型名 | 表記 | 初期値 | 説明
	---|---|---
	ブール型 | Boolean | False | True または False
	長整数型 | Long | 0 | -2,147,483,648 ～ 2,147,483,647 の整数
	倍精度浮動小数点数型 | Double | 0 | 負の値 : 約 -1.8×10<sup>308</sup> ～ -4.0×10<sup>-324</sup><br>正の値 : 約 4.9×10<sup>-324</sup> ～ 1.8×10<sup>308</sup>
	日付型 | Date | #0:00:00# | 日付 : 西暦 100/01/01 ～ 9999/12/31<br>時刻 : 00:00:00 ～ 23:59:59
	文字列型 | String | "" | 任意長さの文字列
	オブジェクト型 | Object | Nothing | 任意のオブジェクト
	レンジ型 | Range | Nothing | セル範囲
	バリアント型 | Variant | Empty | すべてのデータ型

<details>
<summary>あまり使わない変数型</summary>

型名 | 表記 | 初期値 | 説明
---|---|---
バイト型 | Byte | 0 | 0 - 255 の整数
整数 | Integer | 0 | -32,768 - 32,767 の整数
通貨型 | Currency | 0 | -922,337,203,685,477.5808 - 922,337,203,685,477.5807 の固定小数点数
単精度浮動小数点数型 | Single | 0 | 負の値 : 約 -3.4×10<sup>38</sup> ～ -1.4×10<sup>-45</sup><br>正の値 : 約 1.4×10<sup>-45</sup> ～ 1.8×10<sup>38</sup>
</details>

- 主なオブジェクト / コレクション

	<span style="color:red">値格納時は `Set オブジェクト変数名` とする</span>
	
	オブジェクト / コレクション | 内容
	---|---
	Range コレクション | セル, 行, 列 の 1 つ以上のセル範囲を含む選択範囲または 3-D 範囲
	Workbook オブジェクト | Excel ブック
	Workbooks コレクション | 現在、開いているすべての Workbook オブジェクトのコレクション
	Sheets コレクション | 指定されたブックまたは作業中のブックにあるすべてのシートのコレクション
	Worksheet オブジェクト | ワークシート
	Worksheets コレクション | 指定されたブックまたは作業中のブックにあるすべての Worksheet オブジェクトのコレクション
	WorksheetFunction オブジェクト | Visual Basic から呼び出すことができる Excel ワークシート関数のコンテナ
	AutoFilter オブジェクト | 指定されたワークシートのオートフィルタ
	Sort オブジェクト | データの並べ替え
	SortField オブジェクト | Worksheet, ListObject, AutoFIlter オブジェクトのすべての並べ替え情報
	SortFields オブジェクト | SortField オブジェクトのコレクション
	ListObject オブジェクト | ワークシート内のリストオブジェクト
	Error オブジェクト | セル範囲のエラー

- コレクション

	同種のオブジェクトをまとめたもの (コレクションもオブジェクトの一種)。

	```
	' コレクションから任意のオブジェクトを指定
	' (最小インデックス : 1)
	コレクション名.Item(インデックス)    ' 例: Workbooks.Item(1)
	コレクション名(インデックス)         ' 例: Workbooks(1)
	コレクション名.Item(オブジェクト名)  ' 例: Workbooks.Item("Book1.xlsx")
	コレクション名(オブジェクト名)       ' 例: Workbooks("Book1.xls")

	' コレクションの要素数
	コレクション名.Count

	' オブジェクト変数へ値を格納
	Set オブジェクト変数 = オブジェクト

	' オブジェクト変数の破棄
	Set オブジェクト変数 = Nothing
	```

	コレクションオブジェクトのメソッド

	メソッド | 説明
	---|---
	Add | コレクションにメンバ (オブジェクト) を追加
	Item | 指定インデックスまたは名前に対応するメンバを返す
	Remove | 指定インデックスまたは名前に対応するメンバを削除

	コレクション名.Add について

	構文: `コレクション名.Add item, key, before, after`

	属性 | 説明
	---|---
	item | 必須<br>追加するメンバを表す式を指定
	key | 省略可<br>追加するメンバの位置を表す数値の代わりに使用できる重複しない文字列を指定
	before | 省略可<br>指定したメンバの直前に追加
	after | 省略可<br>指定したメンバの直後に追加

- 配列

	```
	' 構文
	Dim 静的配列名([最小インデックス To ]最大インデックス) As データ型
	Dim 動的配列名() As データ型
	' ※ 最小インデックスのデフォルト : 0
	
	' 処理の途中で配列を受ける場合の例
	' → バリアント型で宣言する
	Sub Sample()
	    Dim A As Variant           ' 型、要素数が不明なので Variant 型
	    A = Split("A-B-C", "-")
	    MsgBox A(1)                ' > B
	End Sub
	
	' 動的配列の要素数指定
	ReDim 動的配列名(最大インデックス)             ' > 既存の要素を破棄
	ReDim Preserve 動的配列名(最大インデックス)    ' > 既存の要素を保持
	```


## <a id="statement"></a> ステートメント

- If ～ Then ～ Else

	```
	If 条件式 Then
	    処理
	ElseIf 条件式 Then
	    処理
	Else
	    処理
	End If
	```

- Select Case

	```
	Select Case 値
	    Case 条件
	        処理
	    (Case Else)
	        (処理)
	End Select

	' 条件の例
	' 1 のとき
	Case 1
	' 1, 3, 5 のとき
	Case 1, 3, 5
	' 10 ～ 20 のとき
	Case 10 To 20
	' 10 以上のとき
	Case Is >= 10
	```


- For Next

	```
	For インデックス = 初期値 To 最終値( Step 加算値)
	    処理
	    (If 条件 Then Exit For)
	Next( インデックス)
	```

- For Each

	```
	For Each 要素 In コレクション
	    処理
	    (If 条件 Then Exit For)
	Next( 要素)

	' !!! 注意 !!!
	' コレクションに「配列」を指定するときは、
	' 要素に使う変数をバリアント型で宣言しておくこと !!!
	' 例
	Dim Arr As Variant
	For Each Arr In Split("A-B-C", "-")
	    MsgBox Arr
	Next Arr
	```

- Do .. Loop

	```
	' 繰り返し前に条件判定
	Do 条件式
	    処理
	Loop

	' 繰り返し後に条件判定
	Do
	    処理
	Loop 条件式

	' 処理内の条件判定
	Do
	    処理
	    If 条件 Then Exit Do
	Loop

	' 条件式について
	' 条件が True の時に True を返す
	While 条件

	' 条件が False の時に True を返す
	Until 条件
	```


## <a id="fileOperation"></a> ファイル操作

## <a id="worksheetFunction"></a> ワークシート関数

## <a id="findAndAutofilter"></a> セル検索とオートフィルタ

## <a id="sort"></a> ソート

## <a id="tableOperation"></a> テーブル操作

## <a id="errorHandling"></a> エラー対策

## <a id="debug"></a> デバッグ

