# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
	config.vm.define "consul-server" do |server|
		server.vm.hostname = "consul-server"
		server.vm.box = "hashicorp/precise64"
		server.vm.provision :ansible do |ansible|
			ansible.playbook = "consul.yml"
		end
		server.vm.network "private_network", ip: "192.168.50.4"
	end

	config.vm.define "logstash" do |logstash|
		logstash.vm.hostname = "logstash"
		logstash.vm.box = "hashicorp/precise64"
		logstash.vm.provision :ansible do |ansible|
			ansible.playbook = "logstash.yml"
		end
		
		logstash.vm.provider "vmware_fusion" do |v|
			v.vmx["memsize"] = "2048"
		end

		logstash.vm.network "private_network", ip: "192.168.50.5"
	end

	config.vm.define "client" do |client|
		client.vm.hostname = "client"
		client.vm.box = "hashicorp/precise64"
		client.vm.provision :ansible do |ansible|
			ansible.playbook = "client.yml"
		end
		client.vm.network "private_network", ip: "192.168.50.6"
	end
end
