Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest:25565, host:25565, auto_correct: true
  config.vm.synced_folder "/home/vazogg/Vagrant/Minecraft_Vagrant", "/var/sync/"
  config.vm.hostname = "minecraft"
  # config.ssh.pty = true
config.vm.provider "virtualbox" do |vb|
  vb.memory = "2048"  
  vb.name = "minecraft"
end
config.vm.provision "shell", inline: <<-SHELL
	sudo apt-get update
	sudo apt-get install default-jdk -y
	sudo apt-get install screen -y
	mkdir /home/vagrant/minecraft/
	cd /home/vagrant/minecraft/
	cp /var/sync/server.properties /home/vagrant/minecraft/
	cp /var/sync/ops.json /home/vagrant/minecraft/
	sudo apt-get install wget -y
	wget -O minecraft_server.jar https://s3.amazonaws.com/Minecraft.Download/versions/1.12.2/minecraft_server.1.12.2.jar
	echo "eula=true" > eula.txt
	screen -S "Minecraft server 1"
	java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui &
SHELL
end