# デジタルTV用文字コード(ARIB STD-B24)のiconv変換モジュール
[Opippi さんの gconv-module-aribb24](https://github.com/0p1pp1/gconv-module-aribb24) のビルド・インストール方法だけを改変したものです
それ以外のソースコードは全く同じです

`GCONV_PATH` 環境変数を使うのではなく `iconvconfig` コマンドによりモジュール設定させます
(`man iconvconf` (8) 参照)

## ビルド
OS の iconv 変換モジュールが `/usr/lib/gconv` 以外にある場合 `configure` 実行時に `GCONVSYSDIR` 環境変数にパスを指定します

以下は Debian bullseye の場合の例

``` console
$ ./autogen.sh
$ mkdir build
$ cd build
$ GCONVSYSDIR=/usr/lib/x86_64-linux-gnu/gconv ../configure [--prefix=....]
$ make
```

## インストール
``` console
$ sudo make install
```

### インストール後の確認
``` console
$ make installcheck
```
以下のような出力があれば OK
```
iconv -l | grep ARIB
ARIB-B24//
ARIB-STD-B24//
```

## アンインストール
``` console
$ sudo make uninstall
```

### アンインストール後の確認
``` console
$ make installcheck
```
以下のような出力があればアンインストールされています
```
iconv -l | grep ARIB
make[1]: *** [Makefile:696: installcheck-local] エラー 1
```
