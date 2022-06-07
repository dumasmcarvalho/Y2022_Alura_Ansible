Vagrant.configure("2") do |config|

  config.vm.define "wordpress" do |wordpress|
	  wordpress.vm.network "private_network", ip: "172.17.177.40"
    wordpress.vm.box = "ubuntu/bionic64"

    wordpress.vm.provider "virtualbox" do |vb|
      vb.name = "wordpress"
      vb.cpus = 4
      vb.memory = 2048
    end
  end

  config.vm.define "mysql" do |mysql|
	  mysql.vm.network "private_network", ip: "172.17.177.42"
    mysql.vm.box = "ubuntu/bionic64"

    mysql.vm.provider "virtualbox" do |vb|
      vb.name = "mysql"
      vb.cpus = 2
      vb.memory = 1024
    end
  end

  config.vm.define "ansible" do |ansible|
    ansible.vm.network "private_network", ip: "172.17.177.38"
    ansible.vm.box = "trombik/ansible-ubuntu-20.04-amd64"

    ansible.vm.provider "virtualbox" do |vb|
      vb.name = "ansible"
      vb.cpus = 2
      vb.memory = 1024
    end

    ansible.vm.provision "shell",
    inline: "cp /vagrant/.vagrant/machines/wordpress/virtualbox/private_key /home/vagrant/private_key_wordpress && \
            chmod 600 /home/vagrant/private_key_wordpress && \
            chown vagrant:vagrant /home/vagrant/private_key_wordpress"

    ansible.vm.provision "shell",
    inline: "cp /vagrant/.vagrant/machines/mysql/virtualbox/private_key /home/vagrant/private_key_mysql && \
            chmod 600 /home/vagrant/private_key_mysql && \
            chown vagrant:vagrant /home/vagrant/private_key_mysql"
  end

end