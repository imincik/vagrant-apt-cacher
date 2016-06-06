# -*- mode: ruby -*-
# vi: set ft=ruby :

# Apt-cacher service.
# Ports (guest -> host):
# * 3142 -> 3142


Vagrant.require_version ">= 1.7.4"

box = "bento/ubuntu-16.04"
memory = 521

Vagrant.configure(2) do |config|
    config.vm.box = box

    config.ssh.forward_agent = true
    config.vm.hostname = "apt-cacher"

    config.vm.provision "shell", inline: "apt-get install apt-cacher-ng"

    config.vm.network "forwarded_port",
        guest: 3142,
        host: 3142,
        auto_correct: true

  # VirtualBox
    config.vm.provider "virtualbox" do |vb, override|
        vb.customize ["modifyvm", :id, "--memory", memory]
        vb.customize ["modifyvm", :id, "--nictype1", "virtio"]
    end

    # Parallels
    config.vm.provider "parallels" do |pl, override|
        pl.memory = memory
    end
end

# vim: set ts=4 sts=4 sw=4 et:
