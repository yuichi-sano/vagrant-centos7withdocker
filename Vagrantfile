# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "centos7withdocker"
  config.vm.define 'centos7withdocker' do |node|
    node.vm.hostname = 'centos7withdocker'
  end
  config.vm.network "private_network", ip: "192.168.33.202"
  
  # VitrualBoxの設定、仮想マシンスペック
  config.vm.provider "virtualbox" do |vb|
    # 表示名、GUIの使用、CPU数、メモリ
    vb.name = "centos7withdocker"
    vb.gui = false
    vb.cpus = "4"
    vb.memory = "8192"
  end
end
