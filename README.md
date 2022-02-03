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

### Linus basics 
 - who am I use `uname` / `uname -a` inside our machine
 - where am I `pwd` will give us the default path of our directory
 - list directories/files `ls`
 - list all including hidden folder/file `ls -a`
 - make directory `mkdir name-of-directory`
- navigate to directory `cd name-of-directory` while typing the name press tab to autocomplete
- how to create a file `touch file-name`and confirm with `ls` to see if we have created it
or `nano file-name` to create and edit the file
- how to display content of the file `cat file-name`
- how to remove file `rm -rf file-name` and confirm it with `ls`
- how to copy file `cp file-destination-name final-destination`
- Research on google how to move a file `test.txt` inside `move` folder
- how to check running processes `top` and `ctrl c` to get the terminal back

### Permissions
- Read Write Executable read only
- How to check permissions `ll` or `ls -al`
- change permissions `sudo chmod permissions-file-name` and use `ls` and you can see the colour of that file change indicating that it is executable

When we start automating things, we need to make executable files

### Bash scripting
- `sudo nano provision.sh` sh is the extension. Inside type `#!/bin/bash`
- make provision executable use `sudo chmod +x provision.sh`
- to run all the instructions within the provision.sh file we use `sudo ./provision.sh` . Linux will then start reading the file and seeing `#!/bin/bash` it will understand that this is a bash script

## Manual Installation of all Dependencies

1. To run the tests, in this case we need to go into the environment folder using `cd environment`. We should be able to see the spec-tests folder.
2. Navigate into spec-tests folder where we can see the `Rakefile` which has the RUBY test. Tests are written in RUBY
3. let's install the dependencies for RUBY using `gem install bundler`. gem is the package manager and bundler is the package. Once the command is entered, you can see that gem is installed.
4. run `bundle` - This will install install any dependencies inorder for us to run the test in RUBY.
5. If we run the test within the spec-tests directory using `rake spec` , we can see the number of logs and failures.
6. We get three failures - nodejs, nodejs version 6.1x and pm2. The tests would have failed if we didnt already have git, nginx installed
7. Before we launch the app in this virtual environment, we have to make sure all the tests are passed. We need to install the dependencies inside the VM.
8. Use `sudo apt-get install nodejs -y` to install nodejs
9. To install nodejs version 6.1x, we need to Use `sudo apt-get install python-software-properties` and `curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -` 
10. After this installation, we need to re-run `sudo apt-get install nodejs -y` command. This will pick up the nodejs version 6.1x
11. Use `sudo npm install pm2 -g` to install the package pm2 globally

### Launching the app

- We have to navigate to the synced folder using `cd foldername` and then into the app folder using `cd app` .
- Now from pm2 package, install npm using `npm install` 
- Now use `npm start` . By doing this, we will be able to see the app running in our browser on the specified port
- use `ctrl c` to exit out of the run

### Automating the installation process
1. Go to the provision.sh file and insert the following instructions
```
#!/bin/bash

sudo apt-get update -y

sudo apt-get upgrade -y

sudo apt-get install nginx -y

sudo apt-get install python-software-properties -y

curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -

sudo apt-get install nodejs -y

sudo npm install pm2 -g
```
2. Now having done this, if we run `vagrant up` to create our VM, all the required dependencies will be automatically installed for our environment.
3. Now go into the VM using `vagrant ssh` 
4. got into the synced folder using `cd folder-name` and then into the app folder using `cd app`
5. once you are in the app directory of the synced folder, use `npm install` to launch our app
6. then use `npm start` to see the app running in our browser in the specified port


### Linux Variables
- Create Linux Var `FIRST_NAME=VIVEK` .This will create a variable in linux.
- How to check the var `echo $FIRST_NAME`

### Environment Variables
 - How to check `env var`
 - command: `printenv key` or `env`
 - Create env var `export`
 - `export LAST_NAME=RADHAKRISHNAN`
 - How to make env var persistent?
 - How to delete `env var`. Command: `unset VAR_NAME`
 - How `kill` a process - sudo kill `id`

 ### How to make environmnt persistent
 - In the environment, Use `sudo nano ~/.bashrc` to open up .bashrc
 - Go to the end of the file and add `export Variable=value` and then save and exit
  
 ### Using the grep command
 - `Grep` is an acronym that stands for Global Regular Expression Print.Grep is a Linux / Unix command-line tool used to search for a string of characters in a specified file. The text search pattern is called a regular expression. When it finds a match, it prints the line with the result.
 - use command `grep string-or-word file-name`. This will search for the string/word in that specific file.
 - to search multiple files, use `grep string/word file-name1 filename2 file-name3` etc..

 ### DB CONNECTION REQUIREMENT
 ```
 // connect to database
if(process.env.DB_HOST) {
  mongoose.connect(process.env.DB_HOST);

  app.get("/posts" , function(req,res){
      Post.find({} , function(err, posts){
        if(err) return res.send(err);
        res.render("posts/index" , {posts:posts});
      })
  });
}
```

### Nginx Reverse proxy

- We want to be able to redirect the traffic from port 3000 to port 80, which is the default port with the help of Reverse Proxy for which nginx will used as a web server.
- This can be done use the following steps:
1. use `vagrant up` to create the virtual machine and `vagrant ssh` to access it
2. once in the virtual environment use `sudo nano /etc/nginx/sites-available/default`
3. A new text editor will open up. Scroll down using the keyboard and change the location as following:
```
location / {
                proxy_pass http://localhost:3000;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_cache_bypass $http_upgrade;
    }
```
4. Now save and exit it.
5. Navigate into the synced folder using `cd folder-name` and then into the app folder using `cd app use ` and then use `sudo systemctl restart nginx` to restart 
6. Now use `npm install` and `npm start` . This will have the app running in port 80, which is the default port for web browsers.

## Creating two virtual machines -app and db

1. exit out of the vm and Destroy the VM using `vagrant destroy`

2. Then replace the vagrantfile with the following code:
```
Vagrant.configure("2") do |config|
 config.vm.define "app" do |app|
    app.vm.box = "ubuntu/xenial64"
    app.vm.network "private_network", ip: "192.168.10.100"

    app.vm.synced_folder ".", "/home/vagrant/app"
    app.vm.synced_folder "environment", "/home/vagrant/environment"
    app.vm.provision "shell", path: "provision/provision.sh" , privileged: false
 
  end

 config.vm.define "db" do |db|
    db.vm.box = "ubuntu/xenial64"
    db.vm.network "private_network", ip: "192.168.10.150"

  end

end
```
2. Save it and then use `vagrant up`. This will create the required two VM - app and db.
3. Then use `vagrant ssh app` to access the app vm.
4. use `sudo nano /etc/nginx/sites-available/default` and make the following changes again:
```
location / {
                proxy_pass http://localhost:3000;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_cache_bypass $http_upgrade;
    } 
```
5. Then use `sudo systemctl status nginx` to check if nginx is running or not.
6. Then use `sudo systemctl restart nginx`.
7. use `cd app/app` and then use `npm install` and then `npm start` . This will show that the app is running and we can check this out by going to the web browser and using `192.168.10.100`.



 




