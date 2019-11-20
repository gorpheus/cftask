# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.box_check_update = false

  config.vm.synced_folder ".", "/vagrant", owner: "vagrant", group: "vagrant", mount_options: ["dmode=775,fmode=664"]


  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4098"
	vb.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.become = true
    ansible.playbook = "provision/playbook.yml"
  end

  # ssh agent
  config.ssh.forward_agent = true
end
