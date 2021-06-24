## 概要

msys2でx86_64-w64-mingw32を使用してビルドを行っています。
Windows10 x86_64をターゲットにしています。

ビルドを行ため、一部のソースファイルに変更を行っています。
backspaceや矢印キーがcmd.exeで起動した場合に正しく動作しなかったので一部のソースファイルに変更を行っています。

---

## Configureオプション

以下のオプションでMakefileの作成を行いました。

```
configure --target=<ターゲットアーキテクチャ> --with-expat --enable-static --disable-interprocess-agent
```

---

## ビルド

以下のコマンドでビルドを行いました。

```
make LDFLAGS=-static -j4
```

---

## Appendix

そのままだと、リンクに失敗するため、`make LDFLAGS=-static -j4 -n`でリンクコマンドを確認し、リンクコマンドに`/mingw64/x86_64-w64-mingw32/lib/libbcrypt.a`を追加してリンクを行いました。
