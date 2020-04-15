# -*- mode: ruby -*-
# vi: set ft=ruby :

#================#
# Ansible Server #
#================#

Vagrant.configure("2") do |config|
  config.vm.define "ansible-server" do |cfg|
    cfg.vm.box = "centos/7"
    cfg.vm.provider "virtualbox" do |vb|
      vb.name = "Ansible-Server(github_SysNet4Admin)"
    end
    cfg.vm.host_name = "ansible-server"
    cfg.vm.network "public_network", ip: "192.168.1.10"
    cfg.vm.network "forwarded_port", guest: 22, host: 60010, auto_correct: true, id: "ssh"
    cfg.vm.synced_folder "../data", "/vagrant", disabled: true
    cfg.vm.provision "shell", inline: "yum install ansible -y"
    cfg.vm.provision "file", source: "ansible_env_ready.yml",
      destination: "ansible_env_ready.yml"
    cfg.vm.provision "shell", inline: "ansible-playbook ansible_env_ready.yml"
  end
end