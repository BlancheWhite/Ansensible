Vagrant.configure("2") do |config|

	config.vm.define "VM1" do |subconfig|
		subconfig.vm.box = "centos/7"
		subconfig.ssh.forward_agent = true
		subconfig.vm.network "private_network", ip: "192.168.50.61"
		subconfig.vm.network "forwarded_port", guest: 8080, host: 8080
		subconfig.vm.synced_folder ".", "/shared_folder", type: "virtualbox"
		subconfig.vm.provider "virtualbox" do |vb|
			vb.name = "VM1"
			vb.memory = "512"
			vb.cpus = "1"
			vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
			vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
			end
		
		subconfig.vm.provision "shell", inline: <<-SHELL 
			echo "---------------------------------------------------"
			echo " -- Masina cu CentOS, Git, Java, Maven, Jenkins -- "
			echo "---------------------------------------------------"
			# Hey there! our jorney starts with the mandatory update
			yum -y update
			# Followed by the SSH configuration
			cp /shared_folder/id_rsa /home/vagrant/.ssh/id_rsa;cd /home/vagrant/.ssh;sudo chown vagrant:vagrant id_rsa;sudo chmod 600 id_rsa;
			cp /shared_folder/config /home/vagrant/.ssh/config;cd /home/vagrant/.ssh;sudo chown vagrant:vagrant config;sudo chmod 644 config;
			echo "--SSH Key configuration--"
			pub_key=$( cat /shared_folder_GJMJ/id_rsa.pub )
			grep -q -F "$pub_key" /home/vagrant/.ssh/authorized_keys || echo "$pub_key" >> /home/vagrant/.ssh/authorized_keys

			SHELL
			end
		
	config.vm.define "VM2" do |subconfig|
		subconfig.vm.box = "centos/7"
		subconfig.ssh.forward_agent = true
		subconfig.vm.network "private_network", ip: "192.168.50.62"
		subconfig.vm.network "forwarded_port", guest: 8080, host: 8080
		subconfig.vm.synced_folder ".", "/shared_folder", type: "virtualbox"
		subconfig.vm.provider "virtualbox" do |vb|
			vb.name = "VM2"
			vb.memory = "2048"
			vb.cpus = "1"
			vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
			vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
			end
		subconfig.vm.provision "shell", inline: <<-SHELL 
			echo "---------------------------------------------------"
			echo " -- Masina cu CentOS, Java, Apache, Tomcat -- "
			echo "---------------------------------------------------"
			# Again the update
			yum -y update
			# and the SSH configuration
			cp /shared_folder_JAT/id_rsa /home/vagrant/.ssh/id_rsa;cd /home/vagrant/.ssh;sudo chown vagrant:vagrant id_rsa;sudo chmod 600 id_rsa;
			cp /shared_folder_JAT/config /home/vagrant/.ssh/config;cd /home/vagrant/.ssh;sudo chown vagrant:vagrant config;sudo chmod 644 config;
			pub_key=$( cat /shared_folder_JAT/id_rsa.pub )
			grep -q -F "$pub_key" /home/vagrant/.ssh/authorized_keys || echo "$pub_key" >> /home/vagrant/.ssh/authorized_keys
			chown vagrant:vagrant /home/vagrant/ -R
			
			SHELL
			end
	config.vm.define "VM3" do |subconfig|
		subconfig.vm.box = "centos/7"
		subconfig.ssh.forward_agent = true
		subconfig.vm.network "private_network", ip: "192.168.50.63"
		subconfig.vm.network "forwarded_port", guest: 8080, host: 8080
		subconfig.vm.synced_folder ".", "/shared_folder", type: "virtualbox"
		subconfig.vm.provider "virtualbox" do |vb|
			vb.name = "VM3"
			vb.memory = "2048"
			vb.cpus = "1"
			vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
			vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
			end
		subconfig.vm.provision "shell", inline: <<-SHELL 
			echo "---------------------------------------------------"
			echo " -- Masina cu  -- "
			echo "---------------------------------------------------"
			# Again the update
			yum -y update
			# and the SSH configuration
			cp /shared_folder_JAT/id_rsa /home/vagrant/.ssh/id_rsa;cd /home/vagrant/.ssh;sudo chown vagrant:vagrant id_rsa;sudo chmod 600 id_rsa;
			cp /shared_folder_JAT/config /home/vagrant/.ssh/config;cd /home/vagrant/.ssh;sudo chown vagrant:vagrant config;sudo chmod 644 config;
			pub_key=$( cat /shared_folder_JAT/id_rsa.pub )
			grep -q -F "$pub_key" /home/vagrant/.ssh/authorized_keys || echo "$pub_key" >> /home/vagrant/.ssh/authorized_keys
			chown vagrant:vagrant /home/vagrant/ -R
			
			SHELL
			end	
	end