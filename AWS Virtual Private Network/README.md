## Virtual Private Cloud (VPC)
![Image Link](https://github.com/vivrk2989/eng103a_DevOps/blob/main/Images/VPC-Canva.png)

A virtual private cloud (VPC) is a secure, isolated private cloud hosted within a public cloud. VPC customers can run code, store data, host websites, and do anything else they could do in an ordinary private cloud, but the private cloud is hosted remotely by a public cloud provider. (Not all private clouds are hosted in this fashion.) VPCs combine the scalability and convenience of public cloud computing with the data isolation of private cloud computing.

## CIDR Block
When you create a VPC, you must specify a range of IPv4 addresses for the VPC in the form of a Classless Inter-Domain Routing (CIDR) block; for example, 10.0.0.0/16. This is the primary CIDR block for your VPC.

## Internet Gateway

An internet gateway is a service that allows for internet traffic to actually enter into a VPC.

An Internet Gateway is a logical connection between an AWS VPC and the Internet. It is not a physical device. Each VPC has only one Internet Gateway. If a VPC doesn’t have an Internet Gateway, then the resources cannot be accessed from the Internet.

## Route Table

A route table contains a set of rules, called routes, that are used to determine where network traffic from your subnet or gateway is directed.

A routing table moves the traffic inside a VPC that is coming from the gateway and divides it among subnets.
we can create our own route table to define the flow of traffic within VPC.

## Subnets
When you launch an instance and specify a VPC, the first thing will be, identifying the subnet where this instance need to be launched into. If no subnet is selected, AWS will pick the default subnet within the selected VPC. Once your subnet is identified, the next step will be identifying an Availability Zone.

## NACL
In AWS, a network ACL (or NACL) controls traffic to or from a subnet according to a set of inbound and outbound rules. This means it represents network level security.


