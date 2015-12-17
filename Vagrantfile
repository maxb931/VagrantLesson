Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  # config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "private_network", ip: "10.0.0.200"
  config.vm.network "public_network"

  config.vm.synced_folder "./data/", "/var/www/html/"

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "1024"
    vb.cpus = 2
    vb.customize ["modifyvm", :id, "--cpuexecutioncap", "70"]
    vb.customize ["modifyvm", :id, "--name", "maxburdackivagrantlesson"]
  end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
     sudo apt-get update
     sudo apt-get install -y apache2
     sudo apt-get install -y htop
     sudo apt-get install -y mc
     sudo apt-get install -y maven
     sudo apt-get install -y ant
     sudo add-apt-repository ppa:webupd8team/java
     echo debconf shared/accepted-oracle-license-v1-1 select true | sudo debconf-set-selections
     echo debconf shared/accepted-oracle-license-v1-1 seen true | sudo debconf-set-selections
     sudo apt-get install -y oracle-java8-installer
   SHELL
end





