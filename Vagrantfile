# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.define "trusty" do |machine|
    machine.vm.box = "ubuntu/trusty32"	  
    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    machine.vm.hostname = "kofa.sample.org"
    machine.vm.network "private_network", ip: "192.168.33.33"
    # machine.vm.synced_folder "../data", "/vagrant_data"
    machine.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "2048"
      vb.name = "kofa"
    end
    machine.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "provision.yml"
    end
  end
end