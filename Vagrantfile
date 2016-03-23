# -*- mode: ruby -*-
# vi: set ft=ruby :

unless Vagrant.has_plugin?("vagrant-docker-compose")
  system("vagrant plugin install vagrant-docker-compose")
  puts "Dependencies installed, please try the command again."
  exit
end

Vagrant.configure("2") do |config|
  # VirtualBox defaults
  config.vm.provider "virtualbox" do |v|
       v.gui = false
       v.name = "<App>"
       v.memory = 2048
       v.cpus = 2
  end
  # Private network (required for nfs)
  config.vm.network "private_network", ip: "192.168.99.100"
  # Use NFS for shared folders for better performance
  config.vm.synced_folder '.', '/vagrant', :nfs => { :mount_options => ["dmode=777","fmode=777"] }
  config.vm.box = "ubuntu/trusty64"

  config.vm.provision :docker
  config.vm.provision :docker_compose, yml: ["/vagrant/docker-compose.yml"], project_name: "<App>", run: "always"
  config.vm.provision :shell, :inline => "sed -i 's/GRUB_CMDLINE_LINUX=\"\"/GRUB_CMDLINE_LINUX=\"cgroup_enable=memory swapaccount=1\"/g'  /etc/default/grub"
  config.vm.provision :shell, :inline => "sed -i 's/GRUB_TIMEOUT=5/GRUB_TIMEOUT=0/' /etc/default/grub"
  config.vm.provision :shell, :inline => "update-grub"
  config.vm.provision :shell, :inline => "shutdown -r now"
end
