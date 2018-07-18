# -*- mode: ruby -*-
# vi: set ft=ruby :
require 'yaml'
settings = YAML.load_file 'settings.yml'

puts '---------------------------'
settings.each_pair {|k,v| puts " #{k}: #{v}" }
puts '---------------------------'

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.provider :virtualbox do |vb|
    vb.name = settings['vb_name']
    vb.customize [
      "modifyvm", :id, 
      "--memory", settings['memory'], 
      "--cpus", settings['cpus'], 
      "--ioapic", "on"]
  end
  config.vm.box_check_update = false
  config.vm.network "private_network", ip: settings['host']
  # config.vm.network "public_network"
  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provision "shell", inline: <<-SHELL
  SHELL
end
