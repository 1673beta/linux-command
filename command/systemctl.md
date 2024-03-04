systemctl
===

systemdのserviceを管理するコマンド

## 補足説明

**systemctl**はsystemdを管理するコマンドで、`service`と`chkconfig`が組み合わさったものです。

| 任务 | 旧指令 | 新指令 |
| ---- | ---- | ---- |
| 自動起動を有効 | chkconfig --level 3 httpd on | systemctl enable httpd.service |
| 自動起動を無効 | chkconfig --level 3 httpd off | systemctl disable httpd.service |
| サービスの状態確認 | service httpd status | systemctl status httpd.service （詳細情報）<br> systemctl is-active httpd.service （activeか否か) |
| 起動しているサービスを確認 | chkconfig --list | systemctl list-units --type=service |
| 全てのサービスを確認 | chkconfig --list | systemctl list-unit-files --all|
| サービスを起動 | service httpd start | systemctl start httpd.service |
| サービスを停止 | service httpd stop | systemctl stop httpd.service |
| サービスを再起動 | service httpd restart | systemctl restart httpd.service |
| サービスを再読み込み | service httpd reload | systemctl reload httpd.service |

### 実例

```shell
systemctl start nfs-server.service . # nfsサービスを起動
systemctl enable nfs-server.service # サービスが自動起動するように設定
systemctl disable nfs-server.service # サービスが自動起動しないように設定
systemctl status nfs-server.service # サービスの状態を確認
systemctl restart nfs-server.service # サービスを再起動
systemctl list-units --type=service # 既に起動しているサービスの一覧を確認
```

#### ファイヤーウォールの22番ポートを開く
##### iptables
```shell
iptables -I INPUT -p tcp --dport 22 -j accept
```
##### firewalld
```shell
firewall-cmd --add-port=22/tcp --zone=public --permanent
```

それでもまだ問題がある場合、SELinuxが原因である場合があります。
以下の手順で確認してみてください。

SELinuxの状態を確認する：
```shell
getenforce
```

SELinuxの状態を一時的に変更する：
```shell
setenforce 0 # 一時的にPermissiveにする
```

SElinuxをオフにする：

`/etc/selinux/config`中の`SELINUX=""`をdisabledにし，再起動する。

ファイヤーウォールを完全に停止する：

```shell
sudo systemctl status firewalld.service
sudo systemctl stop firewalld.service          
sudo systemctl disable firewalld.service
```



