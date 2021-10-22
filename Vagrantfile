# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "debian/buster64"
  config.vm.box_version = "10.4.0"
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get --allow-releaseinfo-change update
    sudo apt-get install -y coreutils quilt parted qemu-user-static debootstrap zerofree zip dosfstools bsdtar libcap2-bin grep rsync xz-utils file git curl
    sudo apt-get install -y qemu qemu-user-static binfmt-support
    curl -sSL https://get.docker.com/ | sh
    sudo usermod -aG docker vagrant
    sudo update-binfmts --enable qemu-arm
    systemctl start docker.service

    git clone https://github.com/6za/pi-gen.git  --branch  upstream-rpi-20211022
    chown -R vagrant:vagrant pi-gen
  SHELL
  
end
