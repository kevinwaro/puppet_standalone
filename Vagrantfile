# -*- mode: ruby -*-
Vagrant.configure(2) do |config|

 config.vm.define "puppetserver" do |puppetserver|
   puppetserver.vm.box ="debian/buster64" 
   puppetserver.vm.network "private_network", ip: "192.168.200.10"
   puppetserver.vm.hostname = "puppetserver"
   puppetserver.vm.provider "virtualbox" do |vb|
     vb.memory = "3072"
     vb.cpus = 2
   end
   puppetserver.vm.provision "ansible/puppetserver", type: "ansible" do |ansible|
     ansible.playbook = "ansible/puppet_server.yml"
     ansible.verbose = "v"
     ansible.extra_vars = {
         "target" => "puppetserver",
         "puppet_server_certname" => "puppetserver",
         "puppet_server_name" => "puppetserver",
         "puppet_server_ip" => "192.168.200.10"
     }
    end
 end

 config.vm.define "client" do |client|
   client.vm.box ="debian/bullseye64" 
   client.vm.network "private_network", ip: "192.168.200.11"
   client.vm.hostname = "client"
   client.vm.provider "virtualbox" do |vb|
     vb.memory = "1024"
     vb.cpus = 2
   end
   client.vm.provision "ansible/client", type: "ansible" do |ansible|
     ansible.playbook = "ansible/puppet_agent.yml"
     ansible.verbose = "v"
     ansible.extra_vars = {
         "target" => "client",
         "puppet_agent_certname" => "client",
         "puppet_agent_name" => "client",
         "puppet_server_certname" => "puppetserver",
         "puppet_server_name" => "puppetserver",
         "puppet_server_ip" => "192.168.200.10"
     }
    end
 end
end
