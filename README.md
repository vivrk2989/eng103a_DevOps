# what is DevOPs?
## why DevOps?
### Benefits of DevOps?

**Four pillars of DevOps best practice**
- Ease of Use
- Flexibility
- Robustness - faster delivery of product
- Cost - cost effective

### Monolith, 2 tier & Microservices Architectures

Monolithic applications or systems are characterized by using a single code base for its services and functionalities.

In a microservices architecture, the entire the entire functionality is split up into independently deployable modules which communicate with each other through defined methods called APIs (Application Programming Interfaces).


### Tools required to set up a Virtual Environment (VM)

1. Ruby
2. Vagrant
3. Virtualbox

### 1. Installing RUBY in Windows
- Use the link below to install RUBY
- https://github.com/oneclick/rubyinstaller2/releases/download/RubyInstaller-2.6.6-1/rubyinstaller-devkit-2.6.6-1-x64.exe

- Once set up, use the command `ruby --version` in your git-bash terminal to check the version of RUBY that was installed into your system

### 2. Installing Vagrant

- Use the link below to install vagrant
- https://www.vagrantup.com/

If you are running this on Windows, you will have to do the following things:
- Make sure that if they have Hyper-V disabled. Check via Turn Windows features on or off, and disable it and restart if need be.
- From this point onward to the end of the course, make sure they're ALWAYS running their terminal as an administrator, to make sure they have the rights to access whatever they need.

Once you have vagrant installed you can test it by opening a terminal and typing the following:
- Type `vagrant` in your terminal and you will see the following:
```
vagrant
Usage: vagrant [options] <command> [<args>]

    -v, --version                    Print the version and exit.
    -h, --help                       Print this help.

Common commands:
     box             manages boxes: installation, removal, etc.
     connect         connect to a remotely shared Vagrant environment
     destroy         stops and deletes all traces of the vagrant machine
     global-status   outputs status Vagrant environments for this user
     halt            stops the vagrant machine
     help            shows the help for a subcommand
     hosts           Information about hostnames managed by the vagrant-hosts plugin
     hostsupdater    
     init            initializes a new Vagrant environment by creating a Vagrantfile
     login           log in to HashiCorp\'s Atlas
     package         packages a running vagrant environment into a box
     plugin          manages plugins: install, uninstall, update, etc.
     port            displays information about guest port mappings
     powershell      connects to machine via powershell remoting
     provision       provisions the vagrant machine
     push            deploys code in this environment to a configured destination
     rdp             connects to machine via RDP
     rebuild         plugin: vagrant-digitalocean: destroys and ups the vm with the same ip address
     reload          restarts vagrant machine, loads new Vagrantfile configuration
     resume          resume a suspended vagrant machine
     share           share your Vagrant environment with anyone in the world
     snapshot        manages snapshots: saving, restoring, etc.
     ssh             connects to machine via SSH
     ssh-config      outputs OpenSSH valid configuration to connect to the machine
     status          outputs status of the vagrant machine
     suspend         suspends the machine
     up              starts and provisions the vagrant environment
     vbguest         
     version         prints current and latest Vagrant version

For help on any individual command run `vagrant COMMAND -h`

Additional subcommands are available, but are either more advanced
or not commonly used. To see all subcommands, run the command
`vagrant list-commands`. 
```
- check version of vagrant on git bash with the command below
- `vagrant --version`


### 3. Installing VirtualBox

- Use the link below to install virtualbox
- https://www.virtualbox.org/wiki/Downloads
- This will take you to the homepage from where you need to choose 'windows hosts'

## Steps to follow next
- create a vagrantfile using notepad or `nano vagrantfile` and type the following code in
```
Vagrant.configure("2") do |config|

 config.vm.box = "ubuntu/xenial64"
# creating a virtual machine ubuntu 

# creating a private network with ip 
 config.vm.network "private_network", ip: "192.168.10.100"

end
```
- Run GitBash with admin privileges
- Make sure you are running the command from the location where the vagrantfile is available
- `vagrant up`
- check `vagrant status` 
- It should display "running (virtualbox)"

### Let's create a Virtual Machine 
1. Use `vagrant up` - to create VM
2. Use `vagrant ssh` - Accesing VM
3. Use `sudo apt-get update` - For any software/tool, we need to make sure we have admin permissions. In linux, sudo works the same as running as an administrator. apt-get is linux's package manager.
4. `sudo apt-get update` - for updating any changes 
5. `sudo apt-get upgrade` - To make sure we have upgraded to any further upgrades that we might have missed

### Installing nginx into our VM
6. use `sudo apt-get install nginx` 
7. `exit` - to exit 
8. use `nano vagrantfile` - open up the vagrant file where we can assign an ip address to create a private network between your local host and the VM
9. use `vagrant reload` - to pick up new information. Virtualbox will enforce the newly added changes in vagrantfile inside the VM
10. use `vagrant status` - to see the status
11. use `vagrant ssh` again
12. use `systemctl status nginx` - to check if nginx is working properly


## Commands in Vagrant (Summary)

- create a VM `vagrant up`
- check status `vagrant status`
- delete VM `vagrant destroy`
- pause `vagrant halt`
- to update `vagrant reload` 
- how to access VM `vagrant ssh`
- `systemctl status/restart/start/stop nginx`
- `apt-get package manager install/remove/update/upgrade nginx`
- upgrade - `vagrant upgrade`






