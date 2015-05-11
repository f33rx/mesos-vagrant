# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

ANSIBLE_GROUPS = {
              "master" => ["node1"],
              "nodes" => ["node2", "node3", "node4"],
              "all_groups:children" => ["master", "nodes"]
            }
Vagrant.configure(2) do |config|
    # config.ssh.private_key_path = "~/.ssh/id_rsa"
    config.vm.boot_timeout = 300
    config.vm.box = "boxcutter/centos70"
    config.vm.synced_folder "/Users/nheadleyperdue/src/devops_mesos", "/home/vagrant/devops_mesos"
  #  config.vm.provider "vmware_fusion" do |v|
  #      v.gui = true
  #  end
    config.vm.define "node1" do |node1|
        node1.vm.network :private_network, type: :dhcp 
        node1.vm.network "private_network", ip: "192.168.12.10"
        node1.vm.network "public_network", ip: "192.168.13.10"
        node1.vm.hostname = "node1"
        node1.vm.provision "ansible" do |ansible|
            ansible.playbook = "playbook.yml"
            ansible.groups = ANSIBLE_GROUPS
        end
    end

    config.vm.define "node2" do |node2|
        node2.vm.network "private_network", ip: "192.168.12.11"
        node2.vm.hostname = "node2"
        node2.vm.provision "ansible" do |ansible|
            ansible.playbook = "playbook.yml"
            ansible.groups = ANSIBLE_GROUPS
        end
    end

    config.vm.define "node3" do |node3|
        node3.vm.network "private_network", ip: "192.168.12.12"
        node3.vm.hostname = "node3"
        node3.vm.provision "ansible" do |ansible|
            ansible.playbook = "playbook.yml"
            ansible.groups = ANSIBLE_GROUPS
        end
    end

    config.vm.define "node4" do |node4|
        node4.vm.network "private_network", ip: "192.168.12.13"
        node4.vm.hostname = "node4"
        node4.vm.provision "ansible" do |ansible|
            ansible.playbook = "playbook.yml"
            ansible.groups = ANSIBLE_GROUPS
        end
    end
end
