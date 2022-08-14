# Chapter 03. シェルの便利な機能


## 目次

1. [カーソル移動コマンド](#cursorMovementCommand)

1. [文字の削除](#deleteCharacter)

1. [カットとヤンク](#cut&Yank)

1. [画面表示のロックと解除](#displayLock&Unlock)

1. [強制終了と一時停止](#forcedTermination&Pause)

1. [画面をクリア](#dispalyClear)

1. [コマンド履歴](#commandHistory)


## <a id="cursorMovementCommand"></a> カーソル移動コマンド

コマンド | 内容
---|---
Ctrl + b | 左へ / 文字
Ctrl + f | 右へ / 文字
Alt + b | 左へ / 単語
Alt + f | 右へ / 単語
Ctrl + a | 行頭へ
Ctrl + e | 行末へ


## <a id="deleteCharacter"></a> 文字の削除

コマンド | 内容
---|---
Ctrl + h | カーソル位置の左の文字を削除
Ctrl + d | カーソル位置の文字を削除
Ctrl + w | カーソル位置の左の単語をスペース区切りで削除


## <a id="cut&Yank"></a> カットとヤンク

コマンド | 内容
---|---
Ctrl + k | カーソル位置から行末までを削除
Ctrl + u | カーソル位置から行頭までを削除
Ctrl + y | 最後に削除された内容を貼り付け


## <a id="displayLock&Unlock"></a> 画面表示のロックと解除

コマンド | 内容
---|---
Ctrl + s | 画面表示のロック
Ctrl + q | 画面表示のロックを解除

※ 画面ロック中も、キーボード入力は受け付けられているため、操作には注意が必要


## <a id="forcedTermination&Pause"></a> 強制終了と一時停止

コマンド | 内容
---|---
Ctrl + c | 実行中のジョブの強制終了
Ctrl + z | 実行中のジョブの一時停止

備考  
`jobs` : 実行しているジョブの確認  
`fg` : バックグラウンドジョブをフォアグラウンドジョブに切り替え


## <a id="dispalyClear"></a> 画面をクリア

コマンド | 内容
---|---
Ctrl + l | 画面の内容をクリア (`clear` と同じ)
reset | 端末の初期化


## <a id="commandHistory"></a> コマンド履歴

コマンド | 内容
---|---
Ctrl + p | 前のコマンド履歴を表示
Ctrl + n | 後のコマンド履歴を表示
Ctrl + r | コマンド履歴をインクリメンタル検索

インクリメンタル検索時の操作

コマンド | 内容
---|---
Ctrl + r (1 回目) | インクリメンタル検索開始
(文字入力) | 検索文字を追加
Ctrl + r (2 回目以降) | 前の検索結果を表示
Enter | 検索結果を実行
Esc | 検索結果を表示したまま、プロンプトに戻る
Ctrl + g | 検索結果を破棄して、プロンプトに戻る

