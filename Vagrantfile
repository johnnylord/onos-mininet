Vagrant.configure("2") do |config|

  # Mininet Virtualbox
  config.vm.define "mininet" do |mininet|
    mininet.vm.box = "ktr/mininet"
    mininet.vm.box_version = "1.3.0"
    mininet.vm.network "private_network", ip: "192.168.50.100"
    mininet.vm.provider "virtualbox" do |v|
      v.name = "KTR-Mininet"
      v.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
      v.customize ["modifyvm", :id, "--cpus", "2"]
      v.customize ["modifyvm", :id, "--memory", "2048"]
    end
  end

  # ONOS Controller
  config.vm.define "onos" do |onos|
    onos.vm.box = "ubuntu/xenial64"
    onos.vm.network "private_network", ip: "192.168.50.254"
    onos.vm.network "forwarded_port", guest: 8181, host: 8181
    onos.vm.network "forwarded_port", guest: 80, host: 80
    onos.vm.provider "virtualbox" do |v|
      v.name = "ONOS-Ubuntu1804"
      v.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
      v.customize ["modifyvm", :id, "--cpus", "2"]
      v.customize ["modifyvm", :id, "--memory", "2048"]
    end
  end
end
