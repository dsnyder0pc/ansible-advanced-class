# ansible-advanced-class
Bits of code from the Ansible Advanced - Hands-On - DevOps class I took on Udemy
https://www.udemy.com/course/learn-ansible-advanced/

# Setup Steps
- Install [Virtualbox](https://www.virtualbox.org/wiki/Downloads) and [Vagrant](https://www.vagrantup.com/docs/installation) on your host machine
- (Windows users will want to install [Git](https://git-scm.com/download/win) as well)
- Install Vagrant plugins: `vagrant plugin install vagrant-vbguest vagrant-hostsupdater`
- (Windows users must give themselves modify access to the hosts file: `explorer 'C:\Windows\System32\Drivers\etc'`)
- Clone this repo: `git clone https://github.com/dsnyder0pc/ansible-advanced-class.git`
- Change directory to the repo folder (eg., `cd ansible-advanced-class`)
- run `vagrant up` to launch guests

You'll start with three new virtual machines:
- controller
- db-and-web-server1
- db-and-web-server2

To use the controller for your Ansible work, you'll need to copy
ssh keys to the other hosts. To do that, login to the controller
with: `ssh ansible@192.168.77.71` (or `ssh ansible@controller`)

Once you are logged in, run: `class/copy-ssh-keys.sh`
I've dropped a `class` symlink into the ansible user's homedir for your convenience. This provides convenient access to the invenotry and playboook files that you are working with on the host machine, presumably with a nice IDE. For this class, you'll be running `ansible-playbook` from the `class` folder on the `controller` host. For example:
```
ansible@controller:~$ cd class
ansible@controller:~/class$ ansible-playbook demo1.yaml -i inventory.txt
```
