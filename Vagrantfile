# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.box = "precise64"
  config.vm.network :forwarded_port, host: 80, guest: 80
  config.vm.synced_folder "{{ project_name }}", "/home/vagrant/{{ project_name }}/{{ project_name }}", :owner => "vagrant", :group => "vagrant"
  config.vm.synced_folder "requirements", "/home/vagrant/{{ project_name }}/requirements", :owner => "vagrant", :group => "vagrant"
  config.vm.synced_folder "salt/salt", "/srv/salt"
  config.vm.synced_folder "salt/pillar", "/srv/pillar"

  ## SSH agent forward?
  #config.ssh.forward_agent = true

  ## Salt Provisioner (requires `vagrant gem install vagrant-salt`)
  config.vm.provision :salt do |salt|
    salt.run_highstate = true
    salt.minion_config = "salt/minion.conf"
#    salt.salt_install_type = "git"
#    salt.salt_install_args = "develop"
  end
end
