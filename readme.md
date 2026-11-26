# Health Check: EC2 Status Checks

## Technologies used:

Python, Boto3, AWS, Terraform

## Project Description:

- Create EC2 Instances with Terraform
- Write a Python script that fetches statuses of EC2 Instances and prints to the console
- Extend the Python script to continuously check the status of EC2 Instances in a specific interval

## Screenshots

![Terraform apply](images/terraform-apply.png)  
_`terraform apply` provisions the infrastructure: 10 resources added, including the three EC2 instances._

![dev-vpc in the AWS console](images/vpc.png)  
_The `dev-vpc` (10.0.0.0/16) created by Terraform, shown in the AWS VPC console._

![Three EC2 instances running](images/3-ec2-instances.png)  
_The three EC2 instances (`dev-server`, `dev-server-two`, `dev-server-three`) running as t3.micro in eu-central-1a._

![Instance health check output](images/instance%20health%20check.png)  
_`ec2-status-checks.py` runs on a schedule and prints each instance's state, instance status and system status._

<br>

# Configure EC2 Server Instances: Add Environment Tags

## Technologies used:

Python, Boto3, AWS

## Project Description:

- Write a Python script that automates adding environment tags to all EC2 Server instances

## Screenshots

![Paris instances tagged dev](images/paris-dev.png)  
_`add-env-tags.py` tags every EC2 instance in Europe (Paris), eu-west-3, with `environment: dev`._

![Frankfurt instances tagged prod](images/frankfurt-prod.png)  
_Every EC2 instance in Europe (Frankfurt), eu-central-1, gets the tag `environment: prod`._

<br>

# Automate Displaying EKS Cluster Information

## Technologies used:

Python, Boto3, AWS EKS

## Project Description:

- Write a Python script that fetches and displays EKS cluster status and information

## Screenshots

![EKS cluster created](images/cluster-created.png)  
_The `myapp-eks-cluster` is active in the AWS EKS console, running Kubernetes 1.37._

![EKS node group](images/node-groups.png)  
_The cluster's managed node group runs three t3.micro worker nodes in eu-central-1, all with status Ready._

![Python script output](images/python-cluster-information.png)  
_`eks-status-checks-py` uses Boto3 to fetch the cluster's status, endpoint and Kubernetes version and prints them to the console._

<br>
