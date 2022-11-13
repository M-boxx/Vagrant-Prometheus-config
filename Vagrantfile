#Vagrant-task

# Script for Ansible installation
$ansibleUpScript = <<-'SCRIPT'
echo "Installing script started"
yes | sudo apt-get install ansible
ansible-galaxy collection install community.docker
SCRIPT

Vagrant.configure("2") do |config|

  # Every Vagrant development environment requires a box
  config.vm.box = "generic/ubuntu2004"

  # Create a forwarded port mapping which allows access to a specific port
  config.vm.network "forwarded_port", guest: 3000, host: 3000

  # Setting up ansible environment
  config.vm.provision "shell", inline: $ansibleUpScript


  #Executing the docker+Prometheus installation
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
  
  #Creating user and setting its rules
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "createUserPlaybook.yml"
  end
  
  #Getting physical status (WIP!)
  #config.vm.provision "ansible" do |ansible|
  #  ansible.playbook = "physicalStatusPlaybook.yml"
  #end
  
  #Making cron script
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "cronPlaybook.yml"
  end

end
