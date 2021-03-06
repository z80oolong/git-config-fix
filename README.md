# git 2.17.0 以降において config ファイルの lock に失敗する場合の挙動を変更する差分ファイル

## 概要

分散型バージョン管理システムである [git][GIT_] において、 VFAT ファイルシステム及び [Android OS][ANDR] 及び [Debian noroot 環境][DBNR]における外部ストレージ領域において、 ```git clone``` コマンド等を用いて新しい git リポジトリを作成する場合に、 ```.git/config``` ファイルの lock ファイルについて lock ファイルの権限の変更に失敗するために、 ```.git/config``` の lock に失敗し、リポジトリが作成できない問題が発生しています。

これらの差分ファイルは、 [git][GIT_] において、前述のような ```.git/config``` ファイルの lock に失敗する場合の挙動について、 lock の失敗を無視するかどうかの [git][GIT_] の挙動を設定する事を可能にするための差分ファイルです。

また、 [git][GIT_] のインストール時において、[ハードリンク][LINK]に代えて[シンボリックリンク][SLNK]を使用する修正も同時に加えています。

## 差分ファイルの適用とコンパイル

[git][GIT_] のソースコードに差分ファイルを適用するには、安定版の ```git-x.y.z``` (ここに、x, y, z は安定版のバージョン番号。以下同様。) には、差分ファイル ```git-x.y.z-fix.diff``` を、[github 上の git][GTGH] には、差分ファイル ```git-HEAD-xxxxxxxx-fix.diff``` (ここに、 xxxxxxxx は、 HEAD 版の commit 番号) をそれぞれ適用して下さい。

例えば、安定版の ```git-x.y.z``` のソースコードに ```git-x.y.z-fix.diff``` を適用するには、安定版の ```git-x.y.z``` のソースコードが置かれているディレクトリより、以下のようにして差分ファイル ```git-2.17.0-fix.diff``` を適用します。

```
 $ patch -p1 < /path/to/git-x.y.z-fix.diff
 (ここに、/path/to/diff は、 git-x.y.z-fix.diff が置かれたディレクトリのパス名)
```

なお、以下に示す差分ファイルは、それぞれ右に示す [git][GIT_] の安定版にも適用可能です。

- ```git-2.17.0-fix.diff``` … [git-2.17.1][GIT_], [git-2.17.2][GIT_]
- ```git-2.18.0-fix.diff``` … [git-2.18.1][GIT_]
- ```git-2.19.0-fix.diff``` … [git-2.19.1][GIT_]
- ```git-2.20.0-fix.diff``` … [git-2.20.1][GIT_]

そして、 [github 上の git][GTGH] のソースコードに ```git-HEAD-xxxxxxxx-fix.diff``` を適用するには、安定版の [github 上の git][GTGH] のソースコードが置かれているディレクトリより、以下のようにして差分ファイル ```git-HEAD-xxxxxxxxx-fix.diff``` を適用します。

```
 $ patch -p1 < /path/to/git-HEAD-xxxxxxxx-fix.diff
 (ここに、/path/to/diff は、 git-HEAD-xxxxxxxxx-fix.diff が置かれたディレクトリのパス名)
```

差分ファイルの適用後は、以下のようにして git をコンパイル及びインストールします。

```
 $ make prefix=/path/to/install install CFLAGS="..." LDFLAGS="..."
 (ここに、 /path/to/install は git のインストール先のパス名であり、環境変数 CFLAGS, LDFLAGS は適切な値を設定する。)
```

## 使用法

[git][GIT_] において、 ```.git/config``` ファイルの lock の失敗を無視するかどうかの挙動の設定については、設定項目 ```core.errorLevelConfigLockFailure``` を使用します。 ```core.errorLevelConfigLockFailure``` に設定する各設定値の意味は下記の通りです。

- **```core.errorLevelConfigLockFailure = error```**  
  通常の [git][GIT_] の動作の通り、 lock の失敗時に異常終了します。
- **```core.errorLevelConfigLockFailure = warn```**  
  [git][GIT_] の動作において、 ```.git/config``` ファイルの lock の失敗時に警告メッセージを表示した後、 lock の失敗を無視してリポジトリの作成等を続行します。  
  設定項目 ```core.errorLevelConfigLockFailure``` のデフォルト値です。
- **```core.errorLevelConfigLockFailure = quiet```**  
  [git][GIT_] の動作において、 ```.git/config``` ファイルの lock の失敗時に何もメッセージを表示せず、 lock の失敗を無視してリポジトリの作成等を続行します。

ここで、設定項目 ```core.errorLevelConfigLockFailure``` を変更するには下記のコマンドを実行します。

```
 $ git config --global core.errorLevelConfigLockFailure quiet

 (若しくは、 git config --global core.errorLevelConfigLockFailure error)
 (若しくは、 git config --global core.errorLevelConfigLockFailure warn)
```

なお、 設定項目 ```core.errorLevelConfigLockFailure``` については、設定ファイル ```$HOME/.gitconfig``` を直接編集することでも設定できます。

## 謝辞

なお、これらの差分ファイルの作成に当たっては、 [termux の開発コミュニティ][TERM] による差分ファイルを参考にしました。 [termux の開発コミュニティ][TERM]の皆様には心より感謝致します。

そして、 [Junio C Hamano 氏][JUNI]を始めとした [git の開発コミュニティ][GIT_]の皆様及び [git][GIT_] に関わる全ての方々にも心より感謝致します。

## 使用条件

本差分ファイルは、分散型バージョン管理システムである [git][GIT_] に適用する差分ファイルであり、 [Z.OOL. (mailto:zool@zool.jpn.org)][ZOOL] が著作権を有します。

従って、本差分ファイルは [git][GIT_] のライセンスと同様である [GNU Lesser General Public License 2.1][LGPL] に基づいて配布されるものとします。詳細については、本リポジトリに同梱する ```LICENSE``` を参照して下さい。

<!-- 外部リンク一覧 -->

[DBNR]:https://play.google.com/store/apps/details?id=com.cuntubuntu&hl=ja
[ANDR]:https://www.android.com/intl/ja_jp/
[GIT_]:https://git-scm.com/
[GTGH]:https://github.com/git/git
[LINK]:http://man7.org/linux/man-pages/man2/link.2.html
[SLNK]:http://man7.org/linux/man-pages/man2/symlink.2.html
[TERM]:https://termux.com/
[JUNI]:mailto:gitster@pobox.com
[TAP1]:https://github.com/z80oolong/homebrew-git
[ZOOL]:http://zool.jpn.org/
[LGPL]:http://www.gnu.org/licenses/lgpl-2.1.html
