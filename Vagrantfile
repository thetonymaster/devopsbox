# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"

  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.hostname = "devopsbox"
  config.vm.provision "shell", path: "scripts/bootstrap.sh"

  config.vm.provision "ansible_local" do |ansible|
    ansible.install = false
    ansible.playbook = "ansible/playbook.yml"
    ansible.limit = "devopsbox"
    ansible.inventory_path = "ansible/hosts"
    ansible.verbose = true
    ansible.raw_arguments = "-vvvv -v"
  end
end
