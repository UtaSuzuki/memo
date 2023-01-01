# Ubuntu


## 目次

- [初期設定](initSetting.md)
- [apt コマンドの使い方](cmd_apt.md)
- [root パスワードの設定](#rootPass)

## <a id="rootPass"></a> root パスワードの設定

パスワードを設定することで、[root ログイン](#rootLogin) できるようになる

```sh
$ sudo passwd root
Enter new UNIX password:********
Retype new UNIX password:********
passwd: password updated successfully
```

## <a id="rootLogin"></a> root ログイン

※ [root パスワード](#rootPass) が設定されていること

```sh
$ su -
Passwd:********

#
```
