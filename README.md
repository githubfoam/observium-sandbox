observium-sandbox
=========
observium testing

observium  http://www.observium.org  
vagrant https://www.vagrantup.com  
virtualbox https://www.virtualbox.org

----------------

Playbook
----------------


File:

    - hosts: servers
      roles:
         - observium
         - observium-client
         - src: https://github.com/githubfoam/ansible-role-apache2.git

Command:

git clone this-project  
vagrant up ansi01  
vagrant up control-machine  
control-machine - observium server  
http://192.168.45.20  
login : user/password admin/observium  
ansi01 - observium client  
http://192.168.45.21  
vagrant cloud  
https://app.vagrantup.com/vagrantfoam/boxes/observiumsandbox  
ansible role observium  
https://github.com/githubfoam/ansible-role-observium    


License
-------

GNU General Public License v3.0

Author Information
------------------

An optional section for the role authors
