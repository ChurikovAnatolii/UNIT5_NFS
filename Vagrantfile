# -*- mode: ruby -*-
# vi: set ft=ruby :

# Server

Vagrant.configure("2") do |config|

  config.vm.box = 'almalinux/8'

config.vm.define "server" do |server|

  server.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end
  server.vm.host_name = 'server'
  server.vm.network "public_network"
  (0..3).each do |i|
   server.vm.disk :disk, size: "5GB", name: "disk-#{i}"
  end
 end


# Client

  config.vm.define "client" do |client|
    client.vm.host_name = 'client'
    client.vm.provider :virtualbox do |vb|
      vb.memory = "1024"
    end
    client.vm.network "public_network"
  end

end
