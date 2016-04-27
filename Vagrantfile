# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.define "ci_box" do |node|
    node.vm.box = "ubuntu/wily64"
    node.vm.hostname = "ci_box"
    node.vm.network "private_network", ip: "192.168.50.30"
	
	node.vm.provider :virtualbox do |vb|
	  vb.customize ['modifyvm', :id, '--memory', '2048']
	end
	  
    node.vm.provision "docker" do |docker|
      docker.run "teamcity",
        image: "sjoerdmulder/teamcity",
        args: "-p 8111:8111 -v /vagrant/teamcity:/var/lib/teamcity"
		
	  docker.run "jenkins",
        image: "jenkins",
		args: "-p 8080:8080 -p 50000:50000 -v /vagrant/jenkins:/var/jenkins_home"
    end
  end

end
