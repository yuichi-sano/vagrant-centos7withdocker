# vagrant-centos7withdocker
VirtualBox+Vagrant: CentOs7 
CentOs7: docker
## boxfile
https://github.com/yuichi-sano/vagrant-centos7withdocker/releases/tag/v1

## pre install
1.  VirtualBox
 仮想環境構築ツール
 https://www.virtualbox.org/
2. vagrant
物理・仮想環境統合ツール
https://www.vagrantup.com/downloads.html

上記URLから最新をインストール
### windowsの場合
WindowsBiosの設定で、仮想環境の実行を許可する必要があるかもしれません
## pre serup
### Vagrantがインストールされていることを確認します。
vagrant -v
### Vagrant 必要プラグイン をインストール
※cmdでもpowershellでも可、macだったらzshなど

vagrant plugin update

vagrant plugin install vagrant-vbguest

vagrant plugin install vagrant-disksize

※※Macの場合のみ※※以下コマンドを実行します。

sudo pfctl -ef vagrant-web-packet-filtering.conf

## 仮想環境を構築する場所
### 例（windows）
C:\Users\HOGE\Documents\TESTPJ\

以降の手順は上記ディレクトリ直下にて行います。
## Boxの追加とvagrant初期設定
### ダウンロードしたboxファイルを仮想環境を構築する場所に配置します。
centos7withdocker.boxが
配置されていることが確認できたら下記コマンドを実行します。

※cmdでもpowershellでも可、macだったらzshなど

vagrant box add centos7withdocker centos7withdocker.box

vagrant init centos7withdocker

上記の実施が完了したら

###  本書と同梱されている。VagrantFileを仮想環境を構築する場所に配置します。
### Vagrantを起動します。
vagrant up

## SSH
### 初期ログイン情報

host: 192.168.33.202

port: 22

user: root

pass: vagrant

※ipは不都合があればVagrantFileないに記載されている同IPを変更いただき

vagrant halt

vagrant up  --provision

にてIPを変更ください。

なお、privateIPなので社内などのLANに影響はございません

## 動作確認
sshログインいただき

docker -v

等でversionを確認ください

## rootでインストール済み
git

docker

docker-compose

nginx

phpenv(おまけ)

大きくは上記のみがインストールされています。

必要に応じてyum installしてください。
### 開発のリーディング担当の方
インストールものや、linux上の設定などなど開発メンバに共有する必要がある場合。

vagrant package [package名] --output [box名].box

とかで新たにboxを作ってあげてください。

そのボックスを配布し開発メンバは

vagrant box add [package名] [box名].box

などとし、VagratnFileを良しなに書き換えて起動しなおしをお願いします。

※上記よりも、boxファイルをver管理して、名前は変えずdestoryとかでちゃんと作り直すのをお勧めします。

## TIPS
ホストOSでの**Vagrant**コマンド

-   起動(初回の場合は構築&プロビジョニング&起動)
    
    vagrant up
    
-   vagrant修復
    
    vagrant plugin update
    
-   起動している仮想環境を終了
    
    vagrant halt
    
-   起動(プロビジョニングも実行)
    
    vagrant up --provision
    
-   仮想環境を消去
    
    vagrant destroy default
    vagrant global-status --prune

