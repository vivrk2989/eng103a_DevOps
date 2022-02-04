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


![Image Link](https://github.com/vivrk2989/eng103a_DevOps/blob/main/Images/Development%20environment.png)

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
-----------------------
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
------------------------
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

-----------------
### Linux Variables

![Image Link](https://github.com/vivrk2989/eng103a_DevOps/blob/main/Images/Linux%20variable%20and%20env%20variable.png)

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
----------------
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
--------------
## Creating two virtual machines -app and db

![Image Link](https://github.com/vivrk2989/eng103a_DevOps/blob/main/Images/multi-machine%20env.png)


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

### Installing Dependencies for Mongodb

![Image Link](https://github.com/vivrk2989/eng103a_DevOps/blob/main/Images/Mongodb%20dependency%20installation.png)

1. use `vagrant ssh db` to access the db VM
2. `sudo apt-get update -y` 
3. `sudo apt-get upgrade -y`
4. use `sudo systemctl status mongodb` to check the status and this current point, you wont be able to see it running as we havent installed it yet
5. use `sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927` 
6. use `echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list` 
7. again use `sudo apt-get update -y` and `sudo apt-get upgrade -y`
8. then use `sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20` to install the specific version of mongodb
- use `cd /etc` so that we can access `mongod.conf`
- use `sudo systemctl status mongod` to check the status
- Now use `sudo nano mongod.conf` 
- chnage the `bindIp` to `0.0.0.0` so that the db can cnnect to app and vice-versa
- use `sudo systemctl restart mongod` now to restart the mongod
- Then use `sudo systemctl enable mongod` to enable it
### Creating the DB_HOST variable 
- exit out of the `app` VM
- `vagrant ssh app` to navigate into the app vm to create the DB_HOST variable
- go into the app folder through the synced folder `app` and then make the variable using `export DB _HOST=mongod://192.168.10.150:27017/posts`
- use `printenv DB_HOST` to check if the variable was created
- now `node seeds/seed.js` to get the contents into the browser
- use `npm start` and then go into the browser using `192.168.10.100:3000/posts` to see the browser with the contents


### Automating installation of mongodb dependencies and configuration in mongod.conf
1. Create a provision script with the commands to install the dependencies like below. In this case, `provision` script is made inside the `provisiondb` folder.
```
#!/bin/bash

sudo apt-get update -y

sudo apt-get upgrade -y

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927

echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

sudo apt-get update -y

sudo apt-get upgrade -y

sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

sudo cp /home/vagrant/db/provisiondb/mongod.conf /etc/mongod.conf

sudo systemctl enable mongod

sudo systemctl restart mongod
```
2. let's automate the process of changing the mongod.conf settings
- create a new file called `mongod.conf` inside the `provisiondb` folder and use the following commands. We have made

```
# mongod.conf

# for documentation of all options, see:
#   http://docs.mongodb.org/manual/reference/configuration-options/

# Where and how to store data.
storage:
  dbPath: /var/lib/mongodb
  journal:
    enabled: true
#  engine:
#  mmapv1:
#  wiredTiger:

# where to write logging data.
systemLog:
  destination: file
  logAppend: true
  path: /var/log/mongodb/mongod.log

# network interfaces
net:
  port: 27017
  bindIp: 0.0.0.0


#processManagement:

#security:

#operationProfiling:

#replication:

#sharding:

## Enterprise-Only Options:

#auditLog:

#snmp:
```
3. Once this is done. update the vagrant file as follows with the main chnages being the set up of `db`. A new private_network ip is also given as `192.168.10.150`
```
Vagrant.configure("2") do |config|
 config.vm.define "app" do |app|
    app.vm.box = "ubuntu/xenial64"
    app.vm.network "private_network", ip: "192.168.10.100"

    app.vm.synced_folder ".", "/home/vagrant/app"
    app.vm.provision "shell", path: "provision/provision.sh", privileged: false
 
  end

 config.vm.define "db" do |db|
    db.vm.box = "ubuntu/xenial64"
    db.vm.network "private_network", ip: "192.168.10.150"

    db.vm.synced_folder ".", "/home/vagrant/db"
    db.vm.provision "shell", path: "provisiondb/provision.sh", privileged: false

  end

end
```

4. Use `vagrant up db` to create the vm which automates the process of installing the mongodb dependencies. If you are running for the first time, you don't need to do `vagrant up db --provision`.
5. Now go into /etc directory using `cd /etc` and then use `sudo nano mongod.conf` and look to see if `bindIP: 0.0.0.0. If this is the case, then our automation has worked successfully

### Automating nginx reverse proxy process
1. For `db` vm, we had already automated the process of nginx everse proxy by creating a `mongod.conf` in the same directory as the `provision` script and inserting the following commands

```
# mongod.conf

# for documentation of all options, see:
#   http://docs.mongodb.org/manual/reference/configuration-options/

# Where and how to store data.
storage:
  dbPath: /var/lib/mongodb
  journal:
    enabled: true
#  engine:
#  mmapv1:
#  wiredTiger:

# where to write logging data.
systemLog:
  destination: file
  logAppend: true
  path: /var/log/mongodb/mongod.log

# network interfaces
net:
  port: 27017
  bindIp: 0.0.0.0


#processManagement:

#security:

#operationProfiling:

#replication:

#sharding:

## Enterprise-Only Options:

#auditLog:

#snmp:
```
2. Now lets automate the process of nginx reverse proxy in the app vm.
- We used to do this manually by using the `sudo nano /etc/nginx/sites-available/default` and changing the location section as follows:

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
- But now to automate it, we create a file called `default` in the same directory as the `provison` directory for app and insert the following commands

```
##
# You should look at the following URL's in order to grasp a solid understanding
# of Nginx configuration files in order to fully unleash the power of Nginx.    
# http://wiki.nginx.org/Pitfalls
# http://wiki.nginx.org/QuickStart
# http://wiki.nginx.org/Configuration
#
# Generally, you will want to move this file somewhere, and start with a clean  
# file but keep this around for reference. Or just disable in sites-enabled.    
#
# Please see /usr/share/doc/nginx-doc/examples/ for more detailed examples.     
##

# Default server configuration
#
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        # SSL configuration
        #
        # listen 443 ssl default_server;
        # listen [::]:443 ssl default_server;
        #
        # Note: You should disable gzip for SSL traffic.
        # See: https://bugs.debian.org/773332
        #
        # Read up on ssl_ciphers to ensure a secure configuration.
        # See: https://bugs.debian.org/765782
        #
        # Self signed certs generated by the ssl-cert package
        # Don't use them in a production server!
        #
        # include snippets/snakeoil.conf;

        root /var/www/html;

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                proxy_pass http://localhost:3000/;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_cache_bypass $http_upgrade;
        }

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        #location ~ \.php$ {
        #       include snippets/fastcgi-php.conf;
        #
        #       # With php7.0-cgi alone:
        #       fastcgi_pass 127.0.0.1:9000;
        #       # With php7.0-fpm:
        #       fastcgi_pass unix:/run/php/php7.0-fpm.sock;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #       deny all;
        #}
}


# Virtual Host configuration for example.com
#
# You can move that to a different file under sites-available/ and symlink that
# to sites-enabled/ to enable it.
#
#server {
#       listen 80;
#       listen [::]:80;
#
#       server_name example.com;
#
#       root /var/www/example.com;
#       index index.html;
#
#       location / {
#               try_files $uri $uri/ =404;
#       }
#}
```
3. First `exit` out of the vm and then do `vagrant up app` and then `vagrant ssh app`.
4. Check to see if the above changes are automatically made by using `sudo nano /etc/nginx/sites-available/default`.
5. Th above steps will automate the nginx reverse proxy process.
--------
## Cloud computing
### What is cloud computing?
![Image Link](https://github.com/vivrk2989/eng103a_DevOps/blob/main/Images/Cloud%20computing%20diagram.PNG)

Cloud computing is the delivery of different services through the Internet. These resources include tools and applications like data storage, servers, databases, networking, and software.

Types of clouds:
1. Public
2. Private
3. Hybrid

Cloud computing can be both public and private. Public cloud services provide their services over the Internet for a fee. Private cloud services, on the other hand, only provide services to a certain number of people. There is also a hybrid option, which combines elements of both the public and private services.

Types of Cloud Services
- Email
- Storage, backup, and data retrieval
- Creating and testing apps
- Analyzing data
- Audio and video streaming
- Delivering software on demand

Benefits of Cloud Computing
1. Cost Savings
2. Security
3. Flexibility
4. Mobility
5. Insight
6. Increased Collaboration
7. Quality Control
8. Disaster Recovery
9. Loss Prevention
10. Sustainability

### What is AWS?
AWS (Amazon Web Services) is a comprehensive, evolving cloud computing platform provided by Amazon that includes a mixture of `infrastructure as a service (IaaS)`, `platform as a service (PaaS)` and packaged `software as a service (SaaS)` offerings. AWS services can offer an organization tools such as compute power, database storage and content delivery services

#### How AWS Works?
AWS is separated into different services; each can be configured in different ways based on the user's needs. Users should be able to see configuration options and individual server maps for an AWS service.

The services included are:
- Compute
- Storage databases
- Data management
- Migration
- Hybrid cloud
- Networking
- Development tools
- Management
- Monitoring
- Security
- Governance
- Big data management
- Analytics
- Artificial intelligence (AI)
- Mobile development

#### Benefits of using AWS
- Scalability
- Security
- Reliability
- Flexible and Customizable
- Cost-Effective
----

#### Setting up the AWS Console
- Use the given link, id and password to sign into aws
- Search `ec2` and and select `ec2` from the drop down menu
- Now choose `Launch instance` .
- Now search for ubuntu in the search menu sicne we are using ubuntu for our vm
- Choose `Ubuntu Server 18.04 LTS (HVM), SSD Volume Type - ami-07d8796a2b0f8d29c (64-bit x86) / ami-01ddc0aefcdbc53e7 (64-bit Arm)` and the default `64-bit (x86)
-  Now the next page will ask us to choose an instance type. So the number of servers/number of cpus/how much memory. In this project, no changes are required for this page. Now click `Next: Configure Instance Details`
- This will open up the configure instance details. 1) number of instances - `1`. 2) Subnet - `DevOpsStudent default 1a`. 3) Auto-assign Public ip - `Enable`
- Click `Next Add Storage` . This will give us the option of choosing the storage we require. For a small project, 8GB is sufficient. So click `Next Add Tags`
- In the Add Tags section, type Key - `NAME`, Value - `ENG103A_YourName` . Now click `Next Configure Security Group`
- Here add `eng103a_yourname` in the Security group name and Description. We now have to define rules for the security group we created. So in the rules section, we have to allow access to our ip. So choose my ip from the drop down menu. In the description if needed, add `my ip only`. Then click `Review and Launch`
- After reviewing, click `Launch`. On clicking so, it will ask for a `key pair`. Key can be found in the `eng103a.pem` file which is shared.
- Now the key should be put into the `.ssh` script. So go back into the gitbash terminal. If directory `.ssh` is not created, got out to the home location and use `mkdir .ssh`. Now create a file using `nano eng103a.pem` and copy the Key pari that was shared into it.
- Use `cat eng103a.pem` to check. So we just created the `eng103a.pem` file in our `.ssh` directory.
- Now go back into the browser and choose the correct kep pair name - `eng103a` and  click `launch instances`.
- Click on the instance id and it will bring up the instances dashboard. If no name exists, edit your name next to the instance id like - `eng103a_yourname`.
- Now after choosing your instance, click `connect` on the top right corner.
- `ssh -i "eng103a.pem "ubuntu........eu-west-1.compute.amazonaws.com`, where `ubuntu......` is the machine's id and `eng103a.pem` is the authentication id. This command allows us to ssh into this machine.
- Now go to the gitbash terminal and go into your .ssh directory. Then use `chmod 400 eng103a.pem`. Once done, use `ssh -i "eng103a.pem "ubuntu........eu-west-1.compute.amazonaws.com` . When done first time, it asks to copy the key. So type `yes`. 
- Once this is done, we will land into the `aws ec2 machine`
- To find the name of this machine use `uname -a` 
- Difference between 16.04 and 18.04 is that in 18.04, we don't need to use the `apt-get`. Instead just use `apt`.
- Now run `sudo apt update -y`. Then `sudo apt upgrade -y`
- Then use `sudo apt install nginx -y`. To check status of nginx, use `sudo systemctl status nginx`
- Now go back into the browser and go to the `EC" Instance Connect` tab and copy the `Public ip address` for the instance and put it in the browser. But this will not load nginx page because the port is not open.
- So go back to `EC2` page and click on `instances running` and select your instance and choose the `security` tab where we will configure the secuirty group with the required port.
- Click on the `security group` and then click on `Edit inbound rules`.
- click `Add rule` and select `HTTP` and put source `Anywhere-IPv4`. Give a description if needed like - `public access`. After this is done, click `save rules`.
- Now go back to the browser and refresh the page. This time you will be able to see nginx running on the browser.


### AWS TASK
- Copy data from localhost to ec2 aws
- install required dependencies on ec2 to launch node app
- allow port 3000 in the ssecurity group
--------

1. Get `GitBash` running. Go to your working directory. For eg - `eng103a_DevOps1` 

2. What we wanna do here is to copy our app folder to the aws machine. For this run the following command:
```
scp -i "~/.ssh/eng103a.pem" -r app ubuntu@YOUR_PUBLIC_DNS:~ where Public DNS can be found from your instance in aws.
```
3. Do the same with environment folder using:
```
scp -i "~/.ssh/eng103a.pem" -r environment ubuntu@YOUR_PUBLIC_DNS:~ 
```
4. `SCP` stands for `secure copy`
5. Both the above commands will migrate the app and environment folder to the aws machine.
6. Now go into your .ssh folder using `cd .ssh` and then into your ec2 machine using `ssh -i "eng103a.pem "ubuntu........eu-west-1.compute.amazonaws.com`
7. Install all the dependencies. A list of all the dependencies are below:
```
sudo apt-get update -y

sudo apt-get upgrade -y

sudo apt-get install nginx -y

sudo apt-get install python-software-properties -y

curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -

sudo apt-get install nodejs -y

sudo npm install pm2 -g
```
8. Once this is done, check status of the nginx using `sudo systemctl status nginx` . We should see it running.
9. Now, use `npm install` and `npm start`.
10. We will see it running and listening to port 3000 but we havent provided access to port 3000 in the `security group` section in our `aws instances`.
11. Go back to the `EC2` page and click on `instances running` and select your instance and choose the `security` tab. Here put type as `Custom TCP`, port range as `3000` and give a description and click `Save rules`.
12. Now copy the `Public ip address` for the instance and put it in the browser like - `...........:3000`. This will get the app running.
-----------------
