# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "debian/bookworm64"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  config.vm.network "forwarded_port", guest: 5000, host: 8080

  config.vm.provision "file", source: "./hello.py", destination: "hello.py"
  
  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.

  $script = <<-SCRIPT
  sudo apt update
  sudo apt -y install git nano vim python-is-python3 python3-venv python3-pip
  python -m venv flask_venv
  source flask_venv/bin/activate
  pip install Flask
  SCRIPT
  
  config.vm.provision "shell", inline: $script
end
