# -*- mode: ruby -*-
# vi: set ft=ruby :
#
BOX_NAME = ENV["BOX_NAME"] || "raring"
BOX_URI = ENV["BOX_URI"] || "https://cloud-images.ubuntu.com/vagrant/raring/current/raring-server-cloudimg-amd64-vagrant-disk1.box"
DOKKU_IP = ENV["DOKKU_IP"] || "192.168.34.10"
DOKKU_DOMAIN = ENV["DOKKU_DOMAIN"] || "#{DOKKU_IP}.xip.io"

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = BOX_NAME
  config.vm.box_url = BOX_URI
  config.vm.synced_folder File.dirname(__FILE__), "/dokku"
  config.vm.network :forwarded_port, guest: 80, host: 8088
  config.vm.hostname = DOKKU_DOMAIN
  config.vm.network :private_network, ip: DOKKU_IP

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
  config.vm.provision :shell, :inline => "sudo /dokku/provisioner/bootstrap.sh"
end
