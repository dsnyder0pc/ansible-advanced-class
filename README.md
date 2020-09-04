# ansible-advanced-class
Bits of code from the Ansible Advanced - Hands-On - DevOps class I took on Udemy
https://www.udemy.com/course/learn-ansible-advanced/

# Setup Steps
- Install Virtualbox and Vagrant on your host machine
- Clone this repo
- run `vagrant up` to launch guests

You'll start with three new virtual machines:
- controller
- db-and-web-server1
- db-and-web-server2

To use the controller for your Ansible work, you'll need to copy
ssh keys to the other hosts. To do that, login to the controller
with: `ssh ansible@192.168.77.71`

Once you are logged in, run: `/vagrant/copy-ssh-keys.sh`
