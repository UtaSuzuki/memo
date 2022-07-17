# Ubuntu をインストール (WSL)


## 目次

- [参考](#references)

- [準備](#preparation)

- [各種機能の有効化](#feature_activation)

- [Ubuntu インストール](#install_Ubuntu)

- [Ubuntu を起動](#boot_Ubuntu)

- [Ubuntu をシャットダウン](#shutdown_Ubuntu)


## <a id="references"></a> 参考

- [WSL を使用して Windows に Linux をインストールする](https://docs.microsoft.com/ja-jp/windows/wsl/install)

- [WSL2 のインストール，Ubuntu のインストールと利用（Windows 11 対応の記事）（Windows 上）](https://www.kkaneko.jp/tools/wsl/wsl2.html)

- [Ubuntu インストール後の設定](https://www.kkaneko.jp/tools/ubuntu/ubuntu_setup.html)


## <a id="preparation"></a> 準備

- Windows OS バージョン

  Windows 10 May 2021 Update 以降  
  または  
  Windows 11

- 最新のソフトウェアに更新済み

  Windows Update を実施済みであること


## <a id="feature_activation"></a> 各種機能の有効化

1. 「Windows の機能の有効化または無効化」で、以下の項目にチェックを入れる  
  (場所 : コントロール パネル\プログラム\プログラムと機能)

  - Hyper-V

  - Linux 用 Windows サブシステム  
    (Windows Subsystem for Linux)

  - 仮想マシンプラットフォーム

1. 「OK」でウィンドウを閉じ、画面指示の通りに再起動

1. 管理者として PowerShell を実行

1. Linux 用 Windows サブシステムを有効化

  ```
  > dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
  ```

1. 仮想マシンプラットフォームを有効化

  ```
  > dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
  ```

1. WSL の既定バージョンを "2" に設定

  ```
  > wsl --set-default-version 2
  ```

  ※ このとき、`WSL2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel` などと表示されたら、指示に従い、URL から Linux カーネル更新プログラムパッケージをダウンロードし、インストールする。


## <a id="install_Ubuntu"></a> Ubuntu インストール

1. 管理者権限で PowerShell を起動

1. インストール可能な Linux ディストリビューションを表示

  ```
  > wsl --list --online
  ```

1. Ubuntu をインストール

  ```
  > wsl --install -d <インストール可能な Ubuntu の名前>
  ```

  ※ アンインストールは以下の通り

  ```
  > wsl -l -v
  > wsl --shutdown
  > wsl --unregister <アンインストールする Ubuntu の名前>
  ```

  一応、スタートメニューに残ってないか確認してみること。。。

1. ユーザ名とパスワードを設定

  インストールが完了すると、自動起動し、  
  デフォルトユーザのユーザ名とパスワードの入力を求められる。

1. 完了

  `exit` で終了 (シャットダウン) できる


## <a id="boot_Ubuntu"></a> Ubuntu を起動

1. コマンドで起動

  1. PowerShell を起動

  1. コマンドから Ubuntu を起動

    ```
    > wsl -l -v
    > wsl -d <起動する Ubuntu の名前>
    ```

    ※ カレントディレクトリは、`/mnt/<PowerShell のカレントディレクトリ>` になる。

1. スタートメニューから起動

  すべてのプログラムにインストールした Ubuntu が登録されている。  
  カレントディレクトリは、デフォルトユーザのホームディレクトリになる。

1. 情報確認

  ```sh
  $ cat /etc/os-release

  # または

  $ lsb_release -a
  ```


## <a id="shutdown_Ubuntu"></a> Ubuntu をシャットダウン

```
> wsl -l -v
> wsl -t <DIST-NAME>
> wsl -l -v
```

※ Ubuntu のコンソール上で `exit` (ターミナル終了) しても、`STOPPED` になる。

