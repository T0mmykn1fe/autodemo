# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "autodemodrew" do |autodemodrew|
    autodemodrew.vm.box = "ubuntu/xenial64"
    autodemodrew.vm.network :forwarded_port, guest: 80, host: 8099

    autodemodrew.vm.provision "file", source: "files/tornado.conf", destination: "tornado.conf"
    autodemodrew.vm.provision "file", source: "files/webserver.py", destination: "webserver.py"

    autodemodrew.vm.provision "bootstrap", type: "shell", privileged: true, inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install --assume-yes python-setuptools
      sudo apt-get install --assume-yes python-pip
    SHELL

    # Run Ansible from the Vagrant VM
    autodemodrew.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.install_mode = "pip"
      ansible.verbose = true
      ansible.become = true
    end

    #autodemodrew.vm.provision :ansible do |ansible|
    #  ansible.playbook = "playbook.yml"
    #  ansible.verbose  = true
    #end

  end
end
