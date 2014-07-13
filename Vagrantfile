# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 2
    end

    config.vm.box = "precise32"
    config.vm.box_url = "http://files.vagrantup.com/precise32.box"
    config.vm.network :public_network
    config.vm.network "forwarded_port", guest: 80, host: 8080
    #config.vm.network :private_network, ip: VAGRANT_NETWORK_IP

    config.vm.provision "ansible" do |ansible|
        ansible.host_key_checking = false
        ansible.playbook = "provisioning/site.yml"

        # Enable ssh debugging
        #ansible.verbose = "vvvv"

        # Specify your own inventory file for ansible
        #ansible.inventory_path = "ansible/hosts"
    end

end
