# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--memory", 1024]
    v.customize ["modifyvm", :id, "--cpus", 2]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  config.vm.define "logs" do |logs|
    logs.vm.hostname = "logs"
    logs.vm.network :private_network, ip: "192.168.9.90"

    logs.vm.provision :ansible do |ansible|
      ansible.playbook = "provisioning/elk/playbook.yml"
      ansible.inventory_path = "provisioning/elk/inventory"
      ansible.sudo = true
    end
  end
end
