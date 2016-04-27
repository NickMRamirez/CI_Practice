# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.define "teamcitybox" do |node|
    node.vm.box = "ubuntu/wily64"
    node.vm.hostname = "teamcitybox"
    node.vm.network "private_network", ip: "192.168.3.2"
    node.vm.provision "docker" do |docker|
      docker.run "tc1",
        image: "sjoerdmulder/teamcity",
        args: "-p 8111:8111 -v /vagrant/teamcity:/var/lib/teamcity"
		
	  docker.run "j1",
        image: "jenkins",
        args: "-p 8080:8080 -v /vagrant/jenkins:/var/jenkins_home"

    end
  end

end
