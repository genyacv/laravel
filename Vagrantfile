# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # load config
  _conf = YAML.load(
    File.open(
      File.join(File.dirname(__FILE__), '/ansible/group_vars/vagrant.yml'),
      File::RDONLY
    ).read
  )

  # Box
  config.vm.box = "centos/7"

  # Hostname
  config.vm.hostname = _conf['hostname']

  # Sync
  config.vm.synced_folder ".", "/vagrant", :mount_options => ['dmode=777', 'fmode=755'], type: "virtualbox"

  # Plugin
  if Vagrant.has_plugin?('vagrant-hostsupdater')
    config.hostsupdater.remove_on_suspend = true
    config.hostsupdater.aliases = ["dev-local.jp"]
  end

  if Vagrant.has_plugin?('vagrant-vbguest')
    config.vbguest.auto_update = false
  end

  # Network
  config.vm.network :private_network, ip: _conf['ip']
end
