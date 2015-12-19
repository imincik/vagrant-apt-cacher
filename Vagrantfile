# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.require_version ">= 1.7.0"
BOX = "wily-canonical"
BOX_URL = "http://cloud-images.ubuntu.com/vagrant/wily/current/wily-server-cloudimg-amd64-vagrant-disk1.box"

Vagrant.configure(2) do |config|
  config.vm.box = BOX
  config.vm.box_url = BOX_URL

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", "512"]
    v.customize ["modifyvm", :id, "--nictype1", "virtio"]

    config.vm.network "forwarded_port",
        guest: 3142,
        host: 3142,
        auto_correct: true
    #v.gui = true
  end

  config.vm.hostname = "apt-cacher"
  config.vm.provision "shell", inline: "apt-get install apt-cacher-ng"
end
