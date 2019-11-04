# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "autodemo" do |autodemo|

    autodemo.vm.box = "hashicorp/precise64"

	autodemo.vm.network :forwarded_port, guest: 80, host: 5555

	autodemo.vm.provision "file", source: "files/tornado.conf", destination: "tornado.conf"
	autodemo.vm.provision "file", source: "files/webserver.py", destination: "webserver.py"

    autodemo.vm.provision :ansible do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.verbose  = true
    end

  end

end
