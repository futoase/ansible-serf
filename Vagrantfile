# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

BOX_URL = 'http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_ubuntu-14.04_chef-provisionerless.box'
BOX_NAME = 'bento-Ubuntu-14.04-x86_64'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = BOX_NAME
  config.vm.box_url = BOX_URL
  config.vm.box_check_update = true

  config.vm.network "private_network", ip: "192.168.33.222"

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.customize ["modifyvm", :id, "--memory", "512"]
  end

  config.vm.provision :ansible do |ansible|
    ansible.inventory_path = 'vagrant.box'
    ansible.limit = 'all'
    ansible.playbook = 'site.yml'
    ansible.verbose = 'vvvv'
  end
end
