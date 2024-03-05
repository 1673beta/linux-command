apt
===

Debian系のディストリビューションにおけるパッケージ管理システム 

## 補足説明

**apt**コマンドはDebian系ディストリビューションにおいてAPTソフトウェアパッケージを管理するツールです。**apt-get**や**apt-cache**などに比べよりインタラクティブです。
~~This APT page has Super Cow Powers.~~

### 記法 

```shell
apt [OPTION] PACKAGE
```

### パラメータ(工事中)

```shell
apt update # パッケージ一覧を更新
apt upgrade # パッケージを更新
apt full-upgrade # 保留されたパッケージを更新
apt autoremove # 更新で必要なくなったパッケージを削除
apt install # パッケージやdebをインストール
apt remove # パッケージを削除
apt purge # パッケージと設定を削除
apt show # パッケージの依存関係などを表示
apt search # キーワードを基にパッケージを検索
apt list # 条件を満たすパッケージを表示
apt edit-sources # source.listを編集(**WIP**)
apt clean # キャッシュされている全debファイルを削除
apt autoclean # キャッシュされているがインストールされていないdebファイルを削除
apt moo # 牛が鳴く
```

### オプション(工事中)

#### 共通
```shell
-h, --help 
  コマンドの概要を表示
-v, --version
  プログラムのバージョンを表示
-c, --config-file
  使用するコンフィグファイルを指定。プログラムはデフォルトのコンフィグの後に指定したコンフィグを読み込む。
-o, --option
  任意のコンフィグオプションを設定する。構文は -o Foo::Bar=bar である。異なるオプションを設定するために複数回使用することができる。
```

#### apt upgrade
```shell
-y
  確認をYでスキップする。
```

### 実例(工事中)

パッケージ更新・カーネル更新が来ているか確認する
```shell
sudo apt update
```

更新可能なパッケージ一覧を表示する
```shell
apt list --upgradable
```

パッケージを確認をスキップして更新する
```shell
sudo apt upgrade -y
```

牛を鳴かせる
```shell
apt moo
```

