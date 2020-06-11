# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "base"

  config.vm.define "manager" do |manager|
    manager.vm.box = "centos/8"
    manager.vm.hostname = "manager.example.com"
    manager.vm.network "private_network", ip: "172.16.1.100"
    manager.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "thelinuxthing-ansible-manager"
      vb.memory = "1024"
      vb.cpus = "1"
    end
    manager.vm.provision :shell, inline: <<-SHELL
      yum install vim -y
      ln -s /usr/bin/python3 /usr/bin/python
      sed -i '/PasswordAuthentication/s/no/yes/' /etc/ssh/sshd_config
      sed -i '/PermitRootLogin/s/prohibit-password/yes/' /etc/ssh/sshd_config
    SHELL
  end

  config.vm.define "web1" do |web1|
    web1.vm.box = "centos/7"
    web1.vm.hostname = "web1.example.com"
    web1.vm.network "private_network", ip: "172.16.1.201"
    web1.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "thelinuxthing-ansible-web1"
      vb.memory = "256"
      vb.cpus = "1"
    end
    web1.vm.provision :shell, inline: <<-SHELL
      yum install vim -y
      ln -s /usr/bin/python3 /usr/bin/python
      sed -i '/PasswordAuthentication/s/no/yes/' /etc/ssh/sshd_config
      sed -i '/PermitRootLogin/s/prohibit-password/yes/' /etc/ssh/sshd_config
    SHELL
  end

  config.vm.define "web2" do |web2|
    web2.vm.box = "centos/7"
    web2.vm.hostname = "web2.example.com"
    web2.vm.network "private_network", ip: "172.16.1.202"
    web2.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "thelinuxthing-ansible-web2"
      vb.memory = "256"
      vb.cpus = "1"
    end
    web2.vm.provision :shell, inline: <<-SHELL
      yum install vim -y
      ln -s /usr/bin/python3 /usr/bin/python
      sed -i '/PasswordAuthentication/s/no/yes/' /etc/ssh/sshd_config
      sed -i '/PermitRootLogin/s/prohibit-password/yes/' /etc/ssh/sshd_config
    SHELL
  end

  config.vm.define "db1" do |db1|
    db1.vm.box = "ubuntu/bionic64"
    db1.vm.hostname = "db1.example.com"
    db1.vm.network "private_network", ip: "172.16.1.203"
    db1.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "thelinuxthing-ansible-db1"
      vb.memory = "256"
      vb.cpus = "1"
    end
    db1.vm.provision :shell, inline: <<-SHELL
      ln -s /usr/bin/python3 /usr/bin/python
      sed -i '/PasswordAuthentication/s/no/yes/' /etc/ssh/sshd_config
      echo 'PermitRootLogin yes' >> /etc/ssh/sshd_config
    SHELL
  end

  config.vm.define "db2" do |db2|
    db2.vm.box = "ubuntu/bionic64"
    db2.vm.hostname = "db2.example.com"
    db2.vm.network "private_network", ip: "172.16.1.204"
    db2.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "thelinuxthing-ansible-db2"
      vb.memory = "256"
      vb.cpus = "1"
    end
    db2.vm.provision :shell, inline: <<-SHELL
      ln -s /usr/bin/python3 /usr/bin/python
      echo 'PermitRootLogin yes' >> /etc/ssh/sshd_config
    SHELL
  end
  config.vm.provision :shell, inline: <<-SHELL
    echo root:redhat | chpasswd
    systemctl restart sshd
    echo 172.16.1.100 manager.example.com manager >> /etc/hosts
    echo 172.16.1.201 web1.example.com web1 >> /etc/hosts
    echo 172.16.1.202 web2.example.com web2 >> /etc/hosts
    echo 172.16.1.203 db1.example.com db1 >> /etc/hosts
    echo 172.16.1.204 db2.example.com db2 >> /etc/hosts
   SHELL

end
