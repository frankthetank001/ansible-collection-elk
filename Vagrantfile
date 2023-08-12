# -*- mode: ruby -*-
# vi: set ft=ruby :

NNODES=6

$script = <<-SCRIPT
echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCVFGX7SmtBtE41pieJH8brN3W140g6zKzBxgp4+8e3p3oSKertVnCvRrVJNTg/utjv1GEilPdwpQEV+MR1A1OhweVr/6/UxGLIp+W/3GbyvYii0RKBbI6Dk6L2elCOcbVG8EvlrdaNI8m0/mjyUUfw/jGaOKBmnikWBMHUpJotnDfWXFDBZVZu2WbNY8E5iJjE+axtv/6hH9zna9xHWUENSvoj9/VC68Flxg78ad/SwwL9puMatBvxASj8D6JhpTBzm2vm+VB8ODuQfIT2UVFokVwankqLtNIYShjn+d1sZPR3duv96DW2ybq5hNRGewo3+KMB1AU480h7u5lFsfd4Nui7e8xeQJJkjHm/QUmDrtttdi3v3F+2fAYMvdEY7C/HO2u3Z7TI80pb1nlkkAgTlxIL+8AMvFB6UVuFkxFtZfFXr3ChpfkE8SgdMXQCCczoqpt52TaWZmswKWaTPdRQyj18hw2MSU8lJw7xThBbmVehFNjEDHLLyoEms6UdIbM=" >> /home/vagrant/.ssh/authorized_keys
SCRIPT

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  (0..NNODES - 1).each do |i|
    config.vm.define "k8s-ubuntu-#{i}" do |node|
      #node.vm.box = "ubuntu/focal64"
      node.vm.box = "ubuntu/jammy64"
      node.vm.hostname = "k8s-ubuntu-#{i}"
      config.vm.provider "virtualbox" do |v|
          v.memory = 2048
          v.cpus = 2
      end
      node.vm.network "private_network", ip: "192.168.56.11#{i}"
      node.vm.provision "shell", inline: $script
      node.vm.provision "shell", inline: "echo hello from node #{i}"
    end
  end
end
