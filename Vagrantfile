#!/usr/bin/env ruby
# -*- mode: ruby -*-
# vi: set ft=ruby :
#^syntax detection

Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.2"
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do | vm |
    vm.customize ["modifyvm", :id, "--memory", 1536]
    vm.customize ["modifyvm", :id, "--cpus", "2"]
    vm.customize ["modifyvm", :id, "--ioapic", "on"]
    vm.customize ["modifyvm", :id, "--nictype1", "virtio"]
    vm.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

  config.vm.network :forwarded_port, guest: 4000, host: 4000
  config.vm.network :forwarded_port, guest: 5432, host: 55432

  config.vm.synced_folder "app", "/home/vagrant/app", create: true

  config.vm.provision "shell", path: "https://git.io/v65JW", name: "Firewalld"
  config.vm.provision "shell", path: "https://git.io/v65UF", name: "PostgreSQL"
  config.vm.provision "shell", path: "https://git.io/v65Uk", name: "Erlang"
  config.vm.provision "shell", path: "https://git.io/v65Uq", name: "Elixir"
  config.vm.provision "shell", path: "https://git.io/v65Uy", name: "Phoenix", privileged: false
  config.vm.provision "shell", path: "https://git.io/v65Ui", name: "Node.js", privileged: false
end