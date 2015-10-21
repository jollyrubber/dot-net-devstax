# dot-net-devstax
.NET Development Stack built with Vagrant &amp; Chef

## Install
- [ChefDK](https://downloads.chef.io/chef-dk/)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Vagrant](https://www.vagrantup.com/downloads.html)
- A Git client because Chef may be cloning remote repositories

Verify the ChefDK installation with
```shell
$ chef verify
```
### Vagrant Plugins
The following plugins are required
```shell
$ vagrant plugin install vagrant-berkshelf
$ vagrant plugin install vagrant-omnibus
```
The following plugins are recommended but not required
```shell
$ vagrant plugin install vagrant-hostmanager
$ vagrant plugin install vagrant-vbguest
```
### Create a Windows 2012 R2 Base Box
Use https://github.com/jollyrubber/windows2012r2-packer to create a Windows 2012 R2 base box using packer.

### Startup the Vagrant Box
Assuming you checked out this repository to /php-lamp-devstax
```shell
$ cd /dot-net-devstax
$ vagrant up
```
