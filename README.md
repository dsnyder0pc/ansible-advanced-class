# ansible-advanced-class
Bits of code from the Ansible Advanced - Hands-On - DevOps class I took on Udemy
https://www.udemy.com/course/learn-ansible-advanced/

# Setup Steps
- Install Virtualbox and Vagrant on your host machine
- Install Vagrant plugins: `vagrant plugin install vagrant-vbguest vagrant-hostsupdater`
- Clone this repo: `git clone git@github.com:dsnyder0pc/ansible-advanced-class.git`
- Change directory to the repo folder (eg., `cd ansible-advanced-class`)
- run `vagrant up` to launch guests

You'll start with three new virtual machines:
- controller
- db-and-web-server1
- db-and-web-server2

To use the controller for your Ansible work, you'll need to copy
ssh keys to the other hosts. To do that, login to the controller
with: `ssh ansible@192.168.77.71` (or `ssh ansible@controller`)

Once you are logged in, run: `/vagrant/copy-ssh-keys.sh`
