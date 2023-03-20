# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "cobbler" do |cobbler|
    cobbler.vm.box = "centos/7"
    cobbler.vm.host_name = "cobbler"
    cobbler.vm.network :private_network, ip: "10.0.0.20", virtualbox__intnet: 'pxenet'
    cobbler.vm.network "private_network", ip: "192.168.56.10"
    cobbler.vm.network "forwarded_port", guest: 80, host: 8082
    cobbler.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/cobbler.yml"
    ansible.inventory_path = "ansible/hosts"
    ansible.host_key_checking = "false"
    ansible.limit = "all"
  end
end

  config.vm.define "client" do |client|
    client.vm.box = 'centos/7'
    client.vm.host_name = 'client'
    client.vm.network :private_network, ip: "10.0.0.21", virtualbox__intnet: 'pxenet'
    client.vm.provider :virtualbox do |vb|
      vb.memory = "2048"
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize [
          'modifyvm', :id,
          '--nic1', 'intnet',
          '--intnet1', 'pxenet',
          '--nic2', 'nat',
          '--boot1', 'net',
          '--boot2', 'none',
          '--boot3', 'none',
          '--boot4', 'none'
        ]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end
  end
end
