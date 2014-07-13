VAGRANTFILE_API_VERSION = "2"

Vagrant.configure("2") do |config|

  config.vm.box = 'hashicorp/precise64'

  #La IP 192.168.10.101 será la IP de acceso desde la máquina host
  config.vm.network :private_network, ip: "192.168.10.101"
  config.ssh.forward_agent = true

  #Redirigimos el puerto 80 de la máquina al puerto 8001 de nuestro host
  config.vm.network :forwarded_port, guest: 80, host: 8001

  #Montamos el proyecto en el path /vagrant de la máquina virtual
  config.vm.synced_folder ".", "/vagrant", type: "nfs"

  #Archivo para la preparación de la máquina
  config.vm.provision :shell, :path => "provision.sh"

  #Configurará la maquina con 1GB de RAM y 2 CPUs
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "2", "--ioapic", "on"]
  end

end
