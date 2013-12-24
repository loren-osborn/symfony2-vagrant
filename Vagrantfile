# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_plugin "vagrant-vbguest"

Vagrant::Config.run do |config|

    config.vm.box = "nightly_saucy64"

    config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/saucy/current/saucy-server-cloudimg-amd64-vagrant-disk1.box"

    config.vm.network :hostonly, "10.33.33.10" # Host-Only networking required for nfs shares

    config.vm.share_folder("symfony", "/vagrant", "./", :nfs => false)

    config.vm.provision :puppet do |puppet|
        puppet.manifests_path = "puppet/manifests"
        puppet.module_path = "puppet/modules"
        puppet.options = ['--verbose', '--hiera_config /vagrant/puppet/hiera.yaml']
        # puppet.options = ['--verbose', '--hiera_config /vagrant/puppet/hiera.yaml', '--debug']
	end

end
