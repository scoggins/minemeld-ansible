# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = true


  config.vm.network :forwarded_port, guest: 22, host: 2222, id: "ssh", disabled: true

  # Use the same key for each machine
  

  config.vm.define "minemeld-dev-1604" do |ubuntu1604|
      ubuntu1604.vm.box = "ubuntu/xenial64"
      config.vm.provider "virtualbox" do |vb|
        vb.memory = "1536"
        vb.cpus = "2"
      end
      ubuntu1604.vm.network "forwarded_port", guest: 22, host: 16022, id: "ssh", auto_correct: true
      ubuntu1604.vm.network "forwarded_port", guest: 443, host: 16443, id: "https", auto_correct: true
      ubuntu1604.vm.provision "ansible_local" do |ansible|
        ansible.limit = 'all'
        ansible.playbook = "local.yml"
      end
  end

#  config.vm.define "minemeld-dev-1404" do |ubuntu1404|
#      ubuntu1404.vm.box = "ubuntu/trusty64"
#      ubuntu1404.vm.network "forwarded_port", guest: 22, host: 1422, id: "ssh", auto_correct: true
#      ubuntu1404.vm.provision "ansible_local" do |ansible|
#        ansible.limit = 'all'
#        ansible.playbook = "local.yml"
#      end
#  end

end
