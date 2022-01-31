# what is DevOPs?
## why DevOps?
### Benefits of DevOps?

**Four pillars of DevOps best practice**
- Ease of Use
- 
- Flexibility
- Robustness - faster delivery of product
- Cost - cost effective

### Monolith, 2 tier & Microservices Architectures


### Development Env

```
Vagrant.configure("2") do |config|

 config.vm.box = "ubuntu/xenial64"
# creating a virtual machine ubuntu 

# creating a private network with ip 
 config.vm.network "private_network", ip: "192.168.10.100"

end
```

- create a VM `vagrant up`
- check status `vagrant status`
- delete VM `vagrant destroy`
- pause `vagrant halt`
- to update `vagrant reload` 
- how to access VM `vagrant ssh`
-





