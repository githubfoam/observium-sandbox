# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
# https://docs.observium.org/install_debian/
# Here are some tips for making the most of Ansible and Ansible playbooks.
# https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html
Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "512"
    vb.cpus = 1
  end

  config.vm.define "control-machine" do |webtier|
    webtier.vm.box = "bento/ubuntu-18.04"
    webtier.vm.hostname = "control-machine"
    webtier.vm.network "private_network", ip: "192.168.45.20"
    webtier.vm.network "forwarded_port", guest: 80, host: 80
    webtier.vm.provider "virtualbox" do |vb|
        vb.name = "control-machine"
        vb.memory = "512"
    end
    webtier.vm.provision "shell", inline: <<-SHELL
          sudo apt-get update
          echo "control-machine up && running"
    SHELL
    webtier.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "deploy.yml"
    ansible.become = true
    end
  end






    config.vm.define "ansi01" do |webtier|
      webtier.vm.box = "bento/ubuntu-18.04"
      webtier.vm.hostname = "ansi01"
      webtier.vm.network "private_network", ip: "192.168.45.21"
      webtier.vm.provider "virtualbox" do |vb|
          vb.name = "ansi01"
          vb.memory = "512"
      end
      # https://www.vagrantup.com/docs/provisioning/ansible_local.html
      # ansible-galaxy command is executed by default as vagrant user
      # Setting galaxy_roles_path to a folder like /etc/ansible/roles will fail
      # ansible-galaxy will extract the role a second time in /home/vagrant/.ansible/roles/.
      # if your playbook uses become to run as root, it will fail with a "role was not found" error.
      # To work around that, you can use ansible.galaxy_command to prepend the command with sudo
      webtier.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "deploy01.yml"
      ansible.become = true
      ansible.galaxy_role_file = "/vagrant/requirements.yml"
      ansible.galaxy_roles_path = "/etc/ansible/roles"
      ansible.galaxy_command = "sudo ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path} --force"
      end
      webtier.vm.provision "shell", inline: <<-SHELL
            sudo apt-get update
            echo "ansi01 up && running"
      SHELL
    end

end
