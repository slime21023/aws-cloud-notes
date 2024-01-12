# Create VPC by CLI

### Create a VPC

```bash
aws ec2 create-vpc --cidr-block 172.24.0.0/20
```
The terminal should respond with a bunch of information about this VPC.

Add a **tag** to VPC
```bash
aws ec2 create-tags --resources vpc-id> --tags Key=<tag-key>,Value=<tag-value>
```


### Create public and private subnets

**Subnet** splits large networks into a group of smaller interconnected networks, to reduce traffic congestion and increase routing efficiency.

```bash
aws ec2 create-subnet  --vpc-id <vpc-id> --cidr-block 172.24.1.0/24

# add a tag to subnet
aws ec2 create-tags --resources <subnet-id> --tags Key=<tag-key>,Value-<tag-value>

# add a tag to public subnet
aws ec2 create-tags --resources <subnet-id> --tags Key=Name,Value=public-subnet

aws ec2 create-subnet  --vpc-id <vpc-id> --cidr-block 172.24.2.0/24

# add a tag to private subnet
aws ec2 create-tags --resources <subnet-id> --tags Key=Name,Value=private-subnet
```

### Create internet gateway for the VPC

Internet gateway (IGW) is simply used to connect a VPC to the internet, then VPC resources can access the internet and be accessed over the internet.

```bash
# create internet gateway
aws ec2 create-internet-gateway

# add a tag to internet gateway
aws ec2 create-tags --resources <internet-gateway-id> --tags Key=Name,Value=internet-gateway

### attach the internet gateway to the VPC
aws ec2 atttach-internet-gateway --internet-gateway-id <internet-gateway-id> --vpc-id <vpc-id>
```

### Create an elastic IP address for NAT gateway

An elastic IP address is reserved IPv4 public address that can be assigned to an instance in order to enable communication with the internet.

In order to create a NAT gateway, we'll need an elastic IP address.

```bash
aws ec2 allocate-address --domain vpc
```

### Create a NAT gateway

A  NAT (Netwoerk Address Translation) Gateway is used to enable instances in a private subnet to connect to the internet or other AWS services but prevents the internet from connecting to those  instances.

To create a NAT gateway, need to add the public subnet is which the NAT gateway will reside and also associate the elastic IP address with the NAT gateway.

```bash
aws ec2 create-nat-gateway --subnet-id <public-subnet-id> --allocation-id <elastic-ip-address-id>

# add a tag to the NAT gateway
aws ec2 create-tags --resouces <nat-gateway-id> --tags Key=Name,Value=nat-gateway
```

### Create a route table for each subnet

A route table contains a set of rules this used to determine where the network traffic from the subnets or internet gateway will be directed.

Now, we need two route tables for each subnet.

```bash
aws ec2 create-route-table --vpc-id <vpc-id>

# add a tag to the route table
aws ec2 create-tags --resouces <first-route-table-id> --tags Key=Name,Value=public-route-table

aws ec2 create-route-table --vpc-id <vpc-id>

# add a tag to the route table
aws ec2 create-tags --resouces <second-route-table-id> --tags Key=Name,Value=private-route-table
```

### Create routes

We'll now be creating routes for the previously created route tables.

First attach the table created for the public subnet to the internet gateway. The route matches all IPv4 traffic (0.0.0.0/0) and routes it to the specified Internet gateway.

```bash
aws ec2 create-route --route-table-id <public-route-table-id> --destination-cidr-block 0.0.0.0/0 --gateway-id <internet-gateway-id>
```

Then attach the route table created for the private subnet to the NAT gateway.
The route matches all IPv4 traffic (0.0.0.0/0) and routes it to the specified NAT gateway.

```bash
aws ec2 create-route --route-table-id <private-route-table-id> --destination-cidr-block 0.0.0.0/0 --gateway-id <nat-gateway-id>
```

### Associate route table to subnet

Associate the public route table to the public subnet.

```bash
aws ec2 associate-route-table --route-table-id <public-route-table-id> --subnet-id <public-subnet-id>
```

Associate the private route table to the private subnet.

```bash
aws ec2 associate-route-table --route-table-id <private-route-table-id> --subnet-id <private-subnet-id>
```

### Create a security group for the VPC

Security groups serve as a virtual firewall for instances to control incoming and outgoing traffic.
* Inbound rules control the incoming traffic to the instance
* Outbound rules control the outgoing traffic from the instance.

```bash
aws ec2 create-security-group --group-name <security-group-name> --description "<description>" --vpc-id <vpc-id>

# add a tag to the security group
aws ec2 create-tags --resources <security-group-id> --tags Key=Name,Value=security-group
```

Then, specify rules for the security group created.
* Port 80 allows inbound HTTP access from all IPv4 addresses 
* Port 22 allows inbound SSH access to instances from IPv4 IP addresses in your network

```bash
aws ec2 authorize-security-group-ingress --group-id <security-group-id> --protocol tcp --port 22 --cidr 0.0.0.0/0

aws ec2 authorize-security-group-ingress --group-id <security-group-id> --protocol tcp --port 80 --cidr 0.0.0.0/0
```

### Create Key-pair

Before runnng an instance, we need a key-pair.
*  `keypair`: the name of the key and can be changed to any name.
*  `--output text`: is used to pipe your private key directly into a file.

```bash
aws ec2 create-key-pair --key-name keypair --query 'KeyMaterial' --output text > keypair.pem

# protect your key 
chomd 400 keypair.pem
```

### Run an instance 

An ec2 instance is a virutal server in Amazon's Elastic Compute Cloud (EC2) used for running applications on Amazone web services infrastructure.

```bash
aws ec2 run-instances --image-id <image-id> --instance-type <instance-type> --security-group-ids <security-group-id> --associate-public-ip-address --key-name <keypair-name>

# add a tag to the instance
aws ec2 create-tags --resources <instance-id> --tags Key=<tag-key>,Value=<tag-value>
```





