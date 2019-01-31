# puppetstandalone

## Description

A set of ansible playbooks ran by Vagrant to setup two debian boxes: one running a puppetserver and one runnnig a puppet agent.

I'm using it when I want to write new puppet cookbooks before to deploy them in prod.

## Usage: 

First clone the git repo:

    git clone https://github.com/kevinwaro/puppet_standalone.git && cd puppet_standalone

Then let Vagrant play the music:

    vagrant up
    
Once Vagrant has been ran. You will need to login to the puppet server in order to accept the puppet agent's signing request.

    vagrant ssh puppetserver
    sudo /opt/puppetlabs/puppet/bin/puppet cert sign --all
    
You can now start to write new cookbooks and they will be applied on the agent(s).

You can force it by running the following commands on the client:
    
     vagrant ssh client
     sudo /opt/puppetlabs/puppet/bin/puppet agent -t
     
## Credits:

* author: kevinwaro 
* contact: kevinwaro@yahoo.fr

## Licence

This project is licensed under the GNU GPLv3 License - see the [License.md](License.md) file for details
