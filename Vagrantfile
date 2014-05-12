# -*- mode: ruby -*-
# vi: set ft=ruby :


$script = <<SCRIPT
sed -i 's/^#\\s*\\(%wheel\\s*ALL=(ALL)\\s*NOPASSWD:\\s*ALL\\)/\\1/' /etc/sudoers

useradd alice -g wheel
mkdir -p /home/alice/.ssh
install /vagrant/keys/alice.pem /home/alice/.ssh/alice.pem -m 600
install /vagrant/keys/alice.pub /home/alice/.ssh/authorized_keys -m 644
install /vagrant/keys/ssh_config /home/alice/.ssh/config -m 644
chown -R alice:wheel /home/alice/.ssh

yum install -y --nogpgcheck libselinux-python
SCRIPT


VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "opscode-centos65"
  config.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.5_chef-provisionerless.box"
   
  # VM
  config.vm.define :"an11" do |host|
    host.vm.hostname = "an11"
    host.vm.network :private_network, ip: "192.168.100.11", netmask: "255.255.255.0"
  end

  config.vm.define :"an12" do |host|
    host.vm.hostname = "an12"
    host.vm.network :private_network, ip: "192.168.100.12", netmask: "255.255.255.0"
  end

  config.vm.provision "shell", inline: $script
end
