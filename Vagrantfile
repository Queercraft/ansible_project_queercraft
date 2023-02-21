# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.nfs.functional = false
    config.vm.define "server01" do |host|
        host.vm.box = "generic/ubuntu2204"

        host.vm.hostname = "server01"

        host.vm.network :private_network, ip: "192.168.51.11"
        host.vm.provision :hosts, :sync_hosts => true

        config.vm.provision "shell",
            inline: "ip route add 8.8.8.8/32 dev eth1 > /dev/null 2>&1; /bin/true" # Set ansible_default_ipv4.interface to eth1, needed for keepalived

        config.vm.provider :libvirt do |libvirt|
            libvirt.driver = "kvm"
            libvirt.memory = 4096
            libvirt.cpus = 2
        end
    end
end
