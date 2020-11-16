# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # General Vagrant VM configuration
  config.vm.box = "geerlingguy/ubuntu2004"
  config.ssh.insert_key = false
  config.vm.provider :virtualbox do |v|
    v.memory = 2048
    v.linked_clone = true
  end

  # Mongodb server
  config.vm.define "mongodb" do |mongodb|
    mongodb.vm.hostname = "mongodb"
    mongodb.vm.network :private_network, ip: "192.168.50.5"
  end

  # Frontend server
  config.vm.define "client" do |app|
    app.vm.hostname = "fontend"
    app.vm.network :private_network, ip: "192.168.50.6"
  end

  # Backend server
  config.vm.define "backend" do |backend|
    backend.vm.hostname = "backend"
    backend.vm.network :private_network, ip: "192.168.50.7"
  end

  # Ansible provisioning.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end