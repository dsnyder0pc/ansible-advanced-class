########################################
#
#  Simple script to bootstrap Ansible
#
$script = <<SCRIPT
apt-get update
for pkg in python3 python3-pip python3-apt; do
  dpkg --list $pkg > /dev/null 2>&1 || apt-get install --yes $pkg
done
pip3 install ansible
SCRIPT

VAGRANTFILE_API_VERSION = "2"

########################################
#
#  Define the hosts in our cluster
#  Use a unique IP address for each
#
cluster = {
# Hostname                  Unique IP Address
# -------------------------------------------
  "controller"          =>  "192.168.77.71",
  "db1"                 =>  "192.168.77.72",
  "web1"                =>  "192.168.77.73",
  "web2"                =>  "192.168.77.74",
# -------------------------------------------
}

########################################
#
#  Bring up the cluster
#  Assumes we have an Ansible
#  playbook called baseline.yaml
#
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.provision :shell, inline: $script
  cluster.each_with_index do |(hostname, address), index|
    config.vm.define hostname do |node|
      node.vm.provider :virtualbox do |vb, override|
        vb.linked_clone = true
        override.vm.hostname = hostname
        override.vm.network :private_network, ip: address
        vb.name = hostname
      end
    end
  end
  config.vm.provision :ansible_local do |ansible|
    ansible.verbose = ""
    ansible.become = true
    ansible.playbook = "baseline.yaml"
  end
end
