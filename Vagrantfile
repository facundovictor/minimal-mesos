# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile for testing Ansible scripts and CodeDeploy hook scripts
# Thanks Stack Overflow https://stackoverflow.com/a/25918153/424301
required_plugins = %w( vagrant-vbguest vagrant-triggers )
required_plugins.each do |plugin|
  system "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

default_vagrantbox = "centos/7"
default_playbook   = "ansible/playbook.yml"

vagrantbox = ENV['VAGRANTBOX'] || default_vagrantbox
playbook = ENV['PLAYBOOK'] || default_playbook

Vagrant.configure(2) do |config|
  config.vm.box = vagrantbox

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = 2
  end

  # https://open.mesosphere.com/advanced-course/installing-software/
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.hostname = "mesos"
  config.vm.synced_folder ".",
    "/vagrant",
    type: "virtualbox"

  # https://www.vagrantup.com/docs/provisioning/ansible_local.html
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = playbook
    ansible.verbose  = true
    ansible.install  = true
  end
end
