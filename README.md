restapi-sandbox
=========
observium testing


----------------

Playbook
----------------


File:

    - hosts: servers
      roles:
         - observium
         - observium-client
         - https://github.com/githubfoam/ansible-role-apache2.git

Command:

git clone this-project
vagrant up (control-machine, ansi01) OR  
vagrant up control-machine  
vagrant up ansi01  
control-machine - observium server  
http://192.168.45.20  
login : user/password admin/observium  
ansi01 - observium client  
http://192.168.45.21  
vagrant cloud  
https://app.vagrantup.com/vagrantfoam/boxes/observiumsandbox

License
-------

GNU General Public License v3.0

Author Information
------------------

An optional section for the role authors
