# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

#  if Vagrant.has_plugin?("vagrant-proxyconf")
#    config.proxy.http     = "http://192.168.1.222:3128/"
#    config.proxy.https    = "http://192.168.1.222:3128/"
#    config.proxy.no_proxy = "localhost,127.0.0.1,.example.com"
#  end

#  Vagrant.configure('2') do |config|
#    config.cache.scope = :box
#    config.proxy.enabled = true
#    config.ca_certificates.enabled = true
    # config.ca_certificates.certs = Dir.glob('/etc/pki/ca-trust/source/anchors/*.crt')
#    config.ca_certificates.certs = Dir.glob('/etc/ssl/certs/*.pem')
#  end

  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "fujimakishouten/debian-stretch64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 8180, host: 8180
  config.vm.network "forwarded_port", guest: 8181, host: 8181
  config.vm.network "forwarded_port", guest: 8182, host: 8182

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "10.11.12.13"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  #config.vm.synced_folder ".", "/vagrant", id: "vagrant", type: "nfs", nfs: true, nfs_version: 4, nfs_udp: false
  config.vm.synced_folder ".", "/vagrant", id: "vagrant"
  config.vm.synced_folder "/home/markus/projects/nsbl/", "/nsbl", id: "nsbl"
  config.vm.synced_folder "/home/markus/projects/freckles/", "/freckles", id: "freckles"
  config.vm.synced_folder "/home/markus/projects/inaugurate/", "/inaugurate", id: "inaugurate"
  config.vm.synced_folder "/home/markus/projects/frkl", "/frkl", id: "frkl"

  #config.bindfs.bind_folder "/vagrant/delivery", "/home/vagrant/sites/delivery"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = false
    #vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    wget -O - https://freckles.io | sudo bash -s -- freckles -r gh:makkus/frecklets grav -f /vagrant/ --port 8180 --nginx-user vagrant
  SHELL
  #config.vm.provision :shell, path: "bootstrap.sh", privileged: false
end
