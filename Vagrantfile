# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.provider "virtualbox" do |vb|
    #vb.gui = true
    vb.memory = 3072
    vb.cpus = 2
  end

  ## docker.hl.local
  config.vm.define "docker.hl.local" do |machine|
    machine.vm.hostname = "docker.hl.local"
    machine.vm.box = "centos/7"
    machine.vm.network "private_network", ip: "192.168.57.80"

  end

end
