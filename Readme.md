# puppetstandalone

## Description

A set of ansible playbooks ran by Vagrant to setup two debian boxes: one running a puppetserver and one runnnig a puppet agent.

I'm using it when I want to write new puppet cookbooks before to deploy them in prod.

## Usage: 

First clone the git repo:

    git clone REPO && cd REPO

Then let Vagrant play the music:

    vagrant up
    
Once Vagrant has been ran. You will need to login to the puppet server in order to accept the puppet agent's signing request.

    vagrant ssh server
    sudo /opt/puppetlabs/puppet/bin/puppet cert sign --all
    
You can now start to write new cookbooks and they will be applied on the agent(s).

You can force it by running the following commands on the client:
    
     vagrant ssh client
     sudo /opt/puppetlabs/puppet/bin/puppet agent -t

     
## Credits:

* author: kevinwaro 
* contact: kevinwaro@yahoo.fr

## Licence

Copyright © 2017 kevinwaro <kevinwaro@yahoo.fr>
This work is free. You can redistribute it and/or modify it under the
terms of the Do What The Fuck You Want To Public License, Version 2,
as published by Sam Hocevar. See the COPYING file for more details.