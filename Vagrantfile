ipAddr = "192.168.50.2"
phpVersion = 55

Vagrant.configure(2) do |config|

	#config.vm.provider "virtualbox" do |v|
	#  v.gui = true
	#end
	
	config.vm.box = "relativkreativ/centos-7-minimal"
	
	# install plugin https://github.com/GM-Alex/vagrant-winnfsd (windows nfs support)
	config.vm.network "private_network", ip: ipAddr

	# change path
	config.vm.synced_folder "C:/Users/TAAHESA6/GRV2", "/home/graviton"

	config.vm.provision "shell", path: "init-provisioner.sh", args: phpVersion
	config.vm.provision "shell", inline: "cd /home/graviton/ && php app/console server:status 192.168.50.2:8080 > serverStatus

	if grep -q No serverStatus
	then
		php app/console server:start 192.168.50.2:8080
	else
		php app/console server:stop 192.168.50.2:8080
		php app/console server:start 192.168.50.2:8080
	fi
	rm serverStatus", run: "always", privileged: false
	end

	
	
	
	
	
	
	
	
	
	
	
	
	