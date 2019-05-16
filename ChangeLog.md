# ChangeLog 一覧

本稿では、 [git 2.17.0][GIT_] 以降において VFAT ファイルシステム及び [Android OS][ANDR] 及び [Debian noroot 環境][DBNR]における外部ストレージ領域において、 ```git clone``` コマンド等を用いて新しい git リポジトリを作成する際に ```.git/config``` ファイルの lock に失敗する場合の挙動について、 lock の失敗を無視するかどうかの [git][GIT_] の挙動を設定する事を可能にするための差分ファイルについての変更履歴の一覧を "ChangeLog 一覧" として纏めます。

なお、過去に Gist 上において "追記" として示した変更履歴についても、 "追記" の表記を "ChangeLog" と改め、最新の ChangeLog を先頭に並べ替えた上で再掲してあります。

## 2019/05/15 現在の ChangeLog

2019/05/15 現在の git の [github 上の git の HEAD の commit である ab15ad1a][GIT_]に対応した差分ファイルである ```git-HEAD-ab15ad1a-fix.diff``` を追加致しました。

これに伴い、差分ファイル ```git-HEAD-83232e38-fix.diff``` を削除しました。どうか御了承下さい。

## 2019/05/05 現在の ChangeLog

2019/05/05 現在の git の [github 上の git の HEAD の commit である 83232e38][GIT_]に対応した差分ファイルである ```git-HEAD-83232e38-fix.diff``` を追加致しました。

これに伴い、 ```git-HEAD-0e94f7aa-fix.diff``` を削除しました。どうか御了承下さい。

## 2019/03/20 現在の ChangeLog

2019/03/20 現在の git の[安定版のバージョンの 2.21.0][G210] 及び [github 上の git の HEAD の commit である 0e94f7aa][GIT_]に対応した差分ファイルである ```git-2.21.0-fix.diff, git-HEAD-0e94f7aa-fix.diff``` を追加致しました。

これに伴い、 ```git-2.21.0-fix.diff``` 以外の安定版の差分ファイル及び ```git-HEAD-77556354-fix.diff``` を削除しました。どうか御了承下さい。

## 2019/01/18 現在の ChangeLog

2019/01/18 現在の git の[安定版のバージョンの 2.19.2][G192] と [2.20.0][G200] 及び [github 上の git の HEAD の commit である 77556354][GIT_]に対応した差分ファイルである ```git-2.19.2-fix.diff, git-2.20.0-fix.diff, git-HEAD-fe8321ec-fix.diff``` を追加致しました。

これに伴い、差分ファイル ```git-HEAD-fe8321ec-fix.diff``` を削除しました。どうか御了承下さい。

## 2018/10/08 現在の ChangeLog

2018/10/08 現在の git の[安定版のバージョンの 2.19.0][G180] 及び [github 上の git の HEAD の commit である fe8321ec][GIT_]に対応した差分ファイルである ```git-2.19.0-fix.diff, git-HEAD-fe8321ec-fix.diff``` を追加致しました。

これに伴い、差分ファイル ```git-HEAD-e3331758-fix.diff``` を削除しました。どうか御了承下さい。

## 2018/07/12 現在の ChangeLog

2018/07/12 現在の git の[安定版のバージョンの 2.18.0][GIT_] 及び [github 上の git の HEAD の commit である e3331758][GITH]に対応した差分ファイルである ```git-2.18.0-fix.diff, git-HEAD-e3331758-fix.diff``` を追加致しました。

これに伴い、差分ファイル ```git-HEAD-6f333ff2-fix.diff``` を削除しました。どうか御了承下さい。

なお、これに伴い、 config ファイルの lock に失敗する場合の挙動を変更する [git][GIT_] を導入するための Formula 群である [z80oolong/git][TAP1] を更新しました。こちらの方もどうか御覧下さい。

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
