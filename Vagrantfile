# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
	config.vm.box = "boxcutter/ubuntu1504-desktop"

	config.vm.synced_folder "data", "/vagrant_data"

	config.vm.provider "virtualbox" do |vb|
		# Customize the amount of memory on the VM:
		vb.memory = "1024"
	end

	config.vm.provision "shell", inline: <<-SHELL
		apt-get update
		apt-get -y upgrade
		apt-get install -y curl git openvpn squid
		cp /vagrant_data/proxpn.conf /etc/openvpn/
		cp -r /vagrant_data/ssl /etc/openvpn/
		cp -r /vagrant_data/transmission /home/vagrant/.config/
		chown -R vagrant:vagrant /home/vagrant/.config/transmission
		update-rc.d openvpn remove
		ln -s /vagrant_data/proxpn.sh /home/vagrant/proxpn.sh
	SHELL
end
