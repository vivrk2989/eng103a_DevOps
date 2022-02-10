## Auto Scaling and Load Balancer

Auto scaling automatically adjustss the amount of computational resources based on the server load whereas a load balancer distributes traffic between EC2 instances so that no one instance gets overloaded.

![Image Link](https://github.com/vivrk2989/eng103a_DevOps/blob/main/Images/Auto-Scaling%20and%20load%20balancer%20diagram%20AWS.png)

### Task

1. Create an auto scaling group for our Node app use the app AMI
2. add user data in launch template to launch the node app min 2 instances - max 3 - desired 
3. cpu 25% to send sns and kick in autoscaling group to scale out on demand


- To create a template, use `launch template` and provide a `launch template name`
- Give a description as well
- Click on tags to create a `template tags`
- Scrolling down you will be able to see the `Application and OS Images (Amazon Machine Image)` option where you need to choose the `APP` AMI from `My AMIs`
- Choose `instance type` as `t2.micro`
- Provide the `Key Pair`
- Provide the required `security group name` and its `description`
- Add security rule `HTTP` and `source type` as `Anywhere`
- Add `resource tags` with `key`  and `Value` and Resource type as `Instances` ,`Volumes` and `Network Interfaces`
- Scroll down to `Advanced options` and on the `DNS Hostname` , `Enable` it
- Under user data put these commands

```
#!bin/bash

sudo apt-get update -y
sudo apt-get upgrade -y

cd /home/ubuntu/code/Vagrant/app && screen -d -m npm start
```

- Then choose `Create Launch Templates`

- Now we need to create `Auto Scaling Groups`
- Provide a name to the `Auto Scaling Group` that we are creating
- Use the template that we created with the `APP AMI` 
- On the next Screen, Use the correct VPC - `1a`, `1b`, `1c`
- On the Configure advanced options, click `Attach to a new load balancer`
- Use the `application load balancer` for our app And provide a name to it
-  In the load balancer scheme, use `Internet-facing`
- On the listeners and routing, create a `target group` and provide a name
- On the health check section, enable ELB
- On the configure group size, put desirec capacity size as 2, minimum capacity as 2 and max as 3
- Provide scaling policies
- Provide a name, Choose the metric type and the target value
- Add notification and then add tags
- Then click `create auto scaling group`
- Go to your instances, and choose the right one and copy the ip address 
- Putting this in the browser will get the app running
