Vagrant.configure("2") do |config|
 if Vagrant.has_plugin? "vagrant-vbguest"
 config.vbguest.no_install = true
 config.vbguest.auto_update = false
 config.vbguest.no_remote = true
 end

  config.vm.define :clientefirewall do |clientefirewall|
    clientefirewall.vm.box = "generic/centos9s"
    clientefirewall.vm.network :private_network, ip: "192.168.50.5"
    clientefirewall.vm.hostname = "clientefirewall"
  end


 config.vm.define :servidorfirewall do |servidorfirewall|
 servidorfirewall.vm.box = "generic/centos9s"
 servidorfirewall.vm.network "public_network"
 servidorfirewall.vm.network :private_network, ip: "172.16.0.4"
 servidorfirewall.vm.network :private_network, ip: "192.168.50.4"
 servidorfirewall.vm.hostname = "servidorfirewall"
 end
end
