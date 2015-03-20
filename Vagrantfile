# -*- mode: ruby -*-
# vi: set ft=ruby :

# Set VAGRANT_SERVER_IP variable before running any Vagrant command

# To add additional ip address run following command in shell:
# $ ip addr add <IP address>/24 dev eth1


if ENV["VAGRANT_SERVER_IP"].nil?
  raise "Set VAGRANT_SERVER_IP environment variable before running any Vagrant command !"
end

Vagrant.configure(2) do |config|
  config.vm.box = "precise-canonical"

  config.vm.network "public_network", ip: ENV["VAGRANT_SERVER_IP"]

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--nictype1", "virtio"]
    v.customize ["modifyvm", :id, "--nictype2", "virtio"]
    # v.customize ["modifyvm", :id, "--memory", "1024"]
    # v.gui = true
  end

  config.vm.hostname = "apt-cacher"
  config.vm.provision "shell",
    inline: "
      apt-get install apt-cacher-ng \
      && service apt-cacher-ng restart
    "
end
