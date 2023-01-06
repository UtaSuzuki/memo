# Windows


## 目次

- [Ubuntu をインストール (WSL)](installUbuntu.md)
- [Windows Terminal で Vim の矩形ビジュアルモードにできないときの対処方法](#squareVisualMode)

## <a id="squareVisualMode"></a> Windows Terminal で Vim の矩形ビジュアルモードにできないときの対処方法

settings.json を編集する

1. Windows Terminal のタブ右端の「v」マークをクリックし、「Settings」をクリック
1. ウィンドウ左下の歯車マークをクリック (Visual Studio で編集することが強制される)  
場所：C:\Users\yuta\AppData\Local\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json
1. コードを追加
```diff
         {
             "command": "paste",
             "keys": "ctrl+v"
         },
+        {
+            "command": "null",
+            "keys": "ctrl+v"
+        },
         {
             "command":
             {
```

