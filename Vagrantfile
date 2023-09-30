# -*- mode: ruby -*-
# vi: set ft=ruby :

API_VERSION = "2"
Vagrant.configure(API_VERSION) do |config|
    config.vm.box = "debian/bookworm64"
    config.vm.synced_folder "live_cd", "/home/vagrant/live_cd"
    
    config.vm.provider :virtualbox do |v|
        v.memory = 2048
        v.linked_clone = true
    end

    config.vm.define "live_builder" do |live_builder|
        live_builder.vm.hostname = "live-builder"
        live_builder.vm.network :private_network, ip: "192.168.56.2"
    end
end
