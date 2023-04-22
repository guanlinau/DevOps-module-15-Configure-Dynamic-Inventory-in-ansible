### Demo Project:

Configure Dynamic Inventory

### Technologies used:

Ansible, AWS, Docker, Terraform, Linux

### Project Description:

1- Create AWS EC2 Instance with Terraform

2- Write Ansible Playbook that installs necessary technologies like Docker and Docker Compose, copies docker-compose file to the server

3- Write Ansible AWS EC2 Plugin to dynamically sets inventory of EC2 servers that Ansible should manage, instead of hard-coding server addresses in Ansible inventory file

### Usage instruction

###### Step 1: Create AWS EC2 Instance with Terraform

1-Create a terraform.tfvars file under the root of the current folder with the following variables

```
vpc_cidr_block =
subnet_cidr_block =
availability_zone =
env_profix =
my_ip_address =
instance_type =
public_key_location  =
ssh_private_key_location =
server_user =

```

2-configure aws credentials with specified region and access_id and secret_key

```
cd terrafrom-ec2-instance
```

```
aws configuration
```

3-Configure vpc, ec2 instance server

4- Initialize the Terraform project

```
terraform init
```

5- Create the VPC and EC2 instance , and configure the infrastructure: install

```
terraform apply --auto-approve
```

###### Step 2: Install python3, add boto3, botocore library into requirements.txt

```
python >= 3.6

boto3 >= 1.18.0

botocore >= 1.21.0

```

```
cd ..
```

```
pip install -r requirements.txt
```

###### Step 3: Configure inventory plugin with inventory_aws_ec2.yaml file

###### Step 4: Create docker_deploy_app.yaml

#1 Update yum package, install python3 and docker

#2 Install docker-compose

#3 Start docker deamon

#4 Install python docker docker-compose package module

#5 Add ec2-user to docker group and reset connection

#6 Copy docker-compose.yaml file to ec2 server

#7 Docker login

#8 Start app via docker-compose

###### Step 4: run the ansible

```
ansible-inventory -i inventory_aws_ec2.yaml
```

![image](images/Screenshot%202023-04-22%20at%203.36.35%20pm.png)

```
ansible-playbook docker_deploy_app.yaml
```

![image](images/Screenshot%202023-04-22%20at%202.58.09%20pm.png)
