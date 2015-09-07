# redmine-centos7-mariadb-ansible


最小構成でインストールしたCentOSにRedmineを自動インストールするためのAnsibleプレイブックです。


## 概要 

Ansibleを使ってRedmineを自動インストールするためのプレイブックです。以下のwebサイトで紹介されている手順におおむね準拠しています。

[Redmine 3.1をCentOS 7.1にインストールする手順](http://blog.redmine.jp/articles/3_1/installation_centos/)


## システム構成

* Redmine 3.1
* CentOS 7
* MariaDB
* Apache


## Redmineのインストール手順

インストール直後の CentOS 7 に root でログインし以下の操作を行ってください。


### Ansibleとgitのインストール

```
yum install -y epel-release
yum install -y ansible git
```

### playbookのダウンロード

```
git clone https://github.com/farend/redmine-centos7-mariadb-ansible.git
cd redmine-centos7-mariadb-ansible
```

### MariaDBに設定するパスワードの変更

ファイル `group_vars/redmine-servers` をエディタで開き、 `db_passwd_root` と `db_passwd_redmine` を適当な内容に変更してください。これらはそれぞれ、MariaDBの root ユーザーとRedmine用のユーザー db_redmine に設定されるパスワードです。

### playbook実行

下記コマンドを実行してください。Redmineの自動インストールが開始されます。

```
ansible-playbook -i hosts site.yml
```

10分前後でインストールが完了します。webブラウザで `http://サーバIPアドレス` にアクセスしてください。Redmineの画面が表示されるはずです。 


## ライセンス

MIT License


## 作者

[ファーエンドテクノロジー株式会社](http://www.farend.co.jp/)