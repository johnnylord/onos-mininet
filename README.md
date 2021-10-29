# SDN Experiment Environment

## Create the environment with virtualbox
The following scripts will run up two machines. One is for mininet simulation, the other one is for onos sdn controller.
```shell
vagrant up --provider virtualbox
```

## How to Run
1. Run the ONOS Controller (192.168.50.254)
```bash
$ vagrant ssh onos
# ======== You are in the VM ======
$ cd /home/vagrant/onos-1.15.0/bin
$ ./onos-service start
# =================================
# onos> apps -a -s
# *  27 org.onosproject.optical-model        1.15.0   Optical Network Model
# *  43 org.onosproject.drivers              1.15.0   Default Drivers
# *  49 org.onosproject.hostprovider         1.15.0   Host Location Provider
# *  54 org.onosproject.lldpprovider         1.15.0   LLDP Link Provider
# *  56 org.onosproject.openflow-base        1.15.0   OpenFlow Base Provider
# *  57 org.onosproject.openflow             1.15.0   OpenFlow Provider Suite
# * 162 org.onosproject.fwd                  1.15.0   Reactive Forwarding
```
After that, you are able to access web interface of the controller throught `http://localhost:8181/onos/ui/index.html`. The web service of onos is exported with the vagrant as following: "onos.vm.network "forwarded_port", guest: 8181, host: 8181".

2. Start the mininet simulation
```bash
$ vagrant ssh mininet
$ sudo mn \
    --mac \
    --switch ovsk,protocols=OpenFlow13 \
    --controller=remote,ip=192.168.50.254 \
    --topo linear,2
```
