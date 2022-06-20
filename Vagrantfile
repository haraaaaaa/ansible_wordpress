# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "master-01" do |config|
    config.vm.box = "ubuntu/focal64"
    config.vm.provider "virtualbox" do |vb|
      vb.name = "master-01"
      vb.cpus = 2
      vb.memory = 3072
    end
    config.vm.hostname = "master-01"
    config.vm.network "private_network", ip: "192.168.56.51"
    config.disksize.size = "30GB"
  end
  config.vm.define "web-01" do |config|
    config.vm.box = "ubuntu/focal64"
    config.vm.provider "virtualbox" do |vb|
      vb.name = "web-01"
      vb.cpus = 2
      vb.memory = 3072
    end
    config.vm.hostname = "web-01"
    config.vm.network "private_network", ip: "192.168.56.52"
    config.disksize.size = "30GB"
  end
  config.vm.define "db-01" do |config|
    config.vm.box = "ubuntu/focal64"
    config.vm.provider "virtualbox" do |vb|
      vb.name = "db-01"
      vb.cpus = 2
      vb.memory = 3072
    end
    config.vm.hostname = "db-01"
    config.vm.network "private_network", ip: "192.168.56.53"
    config.disksize.size = "30GB"
  end

  # Hostmanager plugin
  config.hostmanager.enabled = true
  config.hostmanager.manage_guest = true

  # Enable SSH Password Authentication
  config.vm.provision "shell", inline: <<-SHELL
    sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
    sed -i 's/archive.ubuntu.com/ftp.daum.net/g' /etc/apt/sources.list
    sed -i 's/security.ubuntu.com/ftp.daum.net/g' /etc/apt/sources.list
    systemctl restart ssh
  SHELL
end