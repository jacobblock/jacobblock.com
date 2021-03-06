# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    # All Vagrant configuration is done here. The most common configuration
    # options are documented and commented below. For a complete reference,
    # please see the online documentation at vagrantup.com.
  
    # Every Vagrant virtual environment requires a box to build off of.
    config.vm.box = "centos65-x86_64-20140116"
    config.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"
      
    config.vm.hostname = "jacobblock.local"
    config.vm.network "private_network", ip: "192.168.33.10"
  
      # Create a forwarded port mapping which allows access to a specific port
    # within the machine from a port on the host machine. In the example below,
    # accessing "localhost:8080" will access port 80 on the guest machine.
#    config.vm.network "forwarded_port", guest: 80, host: 8080
#    config.vm.network "forwarded_port", guest: 3306, host:13306
  
    # Create a public network, which generally matched to bridged network.
    # Bridged networks make the machine appear as another physical device on
    # your network.
    # config.vm.network "public_network"
  
    config.ssh.forward_agent = true

#    config.hostupdater.aliases = config.vm.hostname
    config.hostsupdater.remove_on_suspend = true

  
    # Share an additional folder to the guest VM. The first argument is
    # the path on the host to the actual folder. The second argument is
    # the path on the guest to mount the folder. And the optional third
    # argument is a set of non-required options.
    # config.vm.synced_folder "../data", "/vagrant_data"
  
    # Provider-specific configuration so you can fine-tune various
    # backing providers for Vagrant. These expose provider-specific options.
    # Example for VirtualBox:
    #
#    config.vm.customize ["modifyvm", :id, "--cpus", "1"]
    config.vm.provider "virtualbox" do |vb|
    #   vb.gui = true

      vb.customize ["modifyvm", :id, "--memory", "512"]
      
    end

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "setup.yml"
#    ansible.inventory_path = "vagrant-inventory"
    ansible.host_key_checking = "false"
  end
end
