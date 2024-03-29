# Chapter 04. ファイルとディレクトリ


## 目次

1. [各ディレクトリの役割](#roleOfEachDirectory)


## <a id="roleOfEachDirectory"></a> 各ディレクトリの役割

Linux のディレクトリ構成は FHS (Filesystem Hierarchy Standard) という標準化仕様に基づく。  
詳細は、[Filesystem Hierarchy Standard](https://www.pathname.com/fhs/) を参照

- /bin

	一般 / 管理ユーザが利用するコマンドの実行ファイルを置くためのディレクトリ。  
	**Linux システムの動作に最低限必要な重要度の高いコマンドを格納**

- /dev

	**デバイスファイルを格納** するディレクトリ。  
	デバイスファイルとは、ディスクやキーボードなどのハードウェアをファイルとして扱えるように用意された特殊なファイルのこと。

- /etc

	設定ファイル (コンフィグファイル) を置くためのディレクトリ。  
	Linux 自体や各種アプリの設定に関わるファイルが置かれている。

- /home

	ユーザ毎に割り当てられる **ホームディレクトリ** が配置されるディレクトリ。  

- /sbin

	/bin と同様に、実行ファイルを置くためのディレクトリ。  
	ただし、こちらには管理者ユーザのコマンドが置かれる。  
	ex) `shutdown` など

- /tmp

	一時的なファイル (テンポラリファイル) を置くためのディレクトリ。  
	このディレクトリ内のファイルを定期的に削除する設定となっているディストリビューションも多い。

- /usr

	各種アプリと、それに付随するファイルを置くためのディレクトリ。  
	追加でアプリをインストールした際に、実行ファイルやドキュメント、ライブラリなどがこのディレクトリに配置される。  
	サブディレクトリには、`bin` `sbin` `etc` などがあり、内部にルートディレクトリ配下と似た構造を持つ。

- /var

	変化する (variable) データを置くためのディレクトリ。  
	アプリを動作する上で作成されたデータやログ、電子メールなどがこのディレクトリに格納される。  
	たくさんのファイルが書き込まれ、容量が逼迫することが多いため、システム管理の上では注意が必要。

