# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Every Vagrant virtual environment requires a box to build off of.
  #config.vm.box = "ubuntu-13.04"
  #config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/raring/current/raring-server-cloudimg-amd64-vagrant-disk1.box"
  
  config.vm.box = 'centos-6-amd64'
  config.vm.box_url = 'https://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.5-x86_64-v20140504.box'
  config.vm.provision "shell", inline: "sudo service iptables stop"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network :forwarded_port, guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network :private_network, ip: "192.168.111.222"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network :public_network

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  #
  # View the documentation for the provider you're using for more
  # information on available options.

  #config.vm.provision "shell", inline: "sudo locale-gen en_US.UTF-8"
  config.vm.provision "ansible" do |ansible|
    ansible.limit = 'all' #https://github.com/mitchellh/vagrant/issues/3096
    ansible.playbook = "playbook.yml"
    ansible.inventory_path = "hosts"
    ansible.host_key_checking = false
    ansible.extra_vars = { ssh_user: 'vagrant' }
  end


end
