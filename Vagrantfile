# -*- mode: ruby -*-
Vagrant.configure(2) do |config|

 config.vm.define "server" do |server|
   server.vm.box ="debian/jessie64" 
   server.vm.network "private_network", ip: "192.168.200.10"
   server.vm.hostname = "server"
   server.vm.provider "virtualbox" do |vb|
     vb.memory = "1024"
     vb.cpus = 1
   end
   server.vm.provision "ansible/server", type: "ansible" do |ansible|
     ansible.playbook = "ansible/puppet_server.yml"
     ansible.verbose = "v"
     ansible.extra_vars = {
         "target" => "server"
     }
    end
 end

 config.vm.define "client" do |client|
   client.vm.box ="debian/jessie64" 
   client.vm.network "private_network", ip: "192.168.200.11"
   client.vm.hostname = "client"
   client.vm.provider "virtualbox" do |vb|
     vb.memory = "512"
     vb.cpus = 1
   end
   client.vm.provision "ansible/client", type: "ansible" do |ansible|
     ansible.playbook = "ansible/puppet_agent.yml"
     ansible.verbose = "v"
     ansible.extra_vars = {
         "target" => "client" 
     }
    end

 end
end
