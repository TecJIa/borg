# -*- mode: ruby -*-
# vim: set ft=ruby :

MACHINES = {
  :otuslinux => {
        :box_name => "ubuntu",
        :vm_name => "passvdvm",
        :ip_addr => '192.168.56.101',		
  },
}
Vagrant.configure("2") do |config|
      config.vm.define "backupvm" do |boxx|
          boxx.vm.box = "ubuntu"
          boxx.vm.host_name = "backupvm"
          #box.vm.network "forwarded_port", guest: 3260, host: 3260+offset
          boxx.vm.network "private_network", ip: '192.168.56.101'
          boxx.vm.provider :virtualbox do |vb|
          vb.memory = 524
          vb.cpus = 1
       end
#         box.vm.disk :disk, size: "1GB", name: "extra_storage"
#	  (0..4).each do |i|
# 	     box.vm.disk :disk, size: "250MB", name: "disk-#{i}"
#    	end
#	end
 	  boxx.vm.provision "shell", inline: <<-SHELL
	      mkdir -p ~root/.ssh
              cp ~vagrant/.ssh/auth* ~root/.ssh
              sudo sed -i 's/\#PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
              systemctl restart sshd
              apt update
#	      apt install -y mdadm smartmontools hdparm fdisk
  	  SHELL
#      end
  end
  config.vm.define "boxname" do |box|
          box.vm.box = "ubuntu"
          box.vm.host_name = "clientdvm"
          #box.vm.network "forwarded_port", guest: 3260, host: 3260+offset
          box.vm.network "private_network", ip: '192.168.56.102'
          box.vm.provider :virtualbox do |vb|
          vb.memory = 524
          vb.cpus = 1
       end
        box.vm.provision "shell", inline: <<-SHELL
	      mkdir -p ~root/.ssh
              cp ~vagrant/.ssh/auth* ~root/.ssh
              sudo sed -i 's/\#PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
              systemctl restart sshd
              apt update
#	      apt install -y mdadm smartmontools hdparm fdisk
  	  SHELL
 end
end
