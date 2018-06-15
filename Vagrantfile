Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest:25565, host:25565, auto_correct: true
  config.vm.synced_folder "/home/vazogg/Vagrant/Apache_Vagrant", "/var/sync/"  
config.vm.provider "virtualbox" do |vb|
  vb.memory = "512"  
end
config.vm.provision "shell", inline: <<-SHELL
  # Packages vom lokalen Server holen
  # sudo sed -i -e"1i deb {{config.server}}/apt-mirror/mirror/archive.ubuntu.com/ubuntu xenial main restricted" /etc/apt/sources.list 
  sudo apt-get update
  sudo apt-get upgrade
  sudo apt install openjdk-8-jre-headless screen
  sudo apt-get -y install a
  
SHELL
end