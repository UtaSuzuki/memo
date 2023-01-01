# Tips

## 目次

- [バージョン確認](#verChk)

## <a id="verChk"></a> バージョンを確認

```sh
$ date
2022年 12月 29日 木曜日 10:11:20 JST

$ which python{,2,3}
/usr/bin/python3

$ ls -la /usr/bin/python3
lrwxrwxrwx 1 root root 9  3月 13  2020 /usr/bin/python3 -> python3.8

$ ls -la /usr/bin | grep python
lrwxrwxrwx  1 root   root          23 11月 14 21:59 pdb3.8 -> ../lib/python3.8/pdb.py
lrwxrwxrwx  1 root   root          31  3月 13  2020 py3versions -> ../share/python3/py3versions.py
lrwxrwxrwx  1 root   root           9  3月 13  2020 python3 -> python3.8
-rwxr-xr-x  1 root   root     5494584 11月 14 21:59 python3.8
```
