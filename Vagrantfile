Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2204"
  config.vm.provider :libvirt do |libvirt|
    libvirt.storage_pool_name = "images"
    libvirt.memory = 1024
    libvirt.cpus = 1
  end

  machines = {
    "zabbix"  => "192.168.51.10",
    "client1" => "192.168.51.11",
    "client2" => "192.168.51.12"
  }

  machines.each do |name, ip|
    config.vm.define name do |machine|
      machine.vm.hostname = name
      machine.vm.network :private_network, ip: ip
    end
  end
end
