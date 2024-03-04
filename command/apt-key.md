apt-key
===

Debian系のディストリビューションでパッケージキーを管理する。

## 補足説明

**apt-key**コマンドはDebian系ディストリビューションでパッケージキーを管理するために用いられます。リリースされたdebパッケージはキーで認証され、apt-keyで管理されます。

apt-keyは**非推奨**になりました。

###  記法

```shell
apt-key(参数)
```

###  パラメータ

操作コマンド: aptキーの操作説明。

###  实例

```shell
apt-key list          # 既に保存されたキーを表示
apt-key add keyname   # ダウンロードしたキーをローカルの信頼できるDBに保存
apt-key del keyname   # ローカルの信頼できるDBからキーを削除
apt-key update        # ローカルの信頼できるDBを更新し、期限切れのキーを削除
```


