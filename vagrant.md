  
# Vagrant cheat sheet  

- [Quick start tutorial](https://learn.hashicorp.com/collections/vagrant/getting-started)

## Most used commands:  
- `vagrant init hashicorp/bionic64`		Create a VM in virtualbox running ubuntu 18.04 LTS 64bit  
- `vagrant up`		start VM  
- `vagrant ssh`		SSH into the machine  
- `logout` or `CTRL+D`		leave the SSH session  
- `vagrant destroy`		terminate the VM. It does not remove downloaded boxes  

Box managing
- `vagrant box list`		list boxes  
- `vagrant box remove [BOX NAME]`		removes the box.


