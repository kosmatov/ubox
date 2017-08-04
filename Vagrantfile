# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.hostname = "dbox"
  config.vm.box = "ubuntu/xenial64"

  config.vm.network :private_network, ip: "10.0.1.33"

  config.vm.synced_folder "~", "/host", type: "nfs"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.vm.provision "ansible" do |an|
    an.playbook = "dev.yml"
  end

  config.ssh.forward_agent = true
  config.ssh.keep_alive = true
  # config.ssh.private_key_path = "~/.ssh/id_rsa"
end
