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

# Data Backup & Restore

## Technologies used:

Python, Boto3, AWS

## Project Description:

- Write a Python script that automates creating backups for EC2 Volumes
- Write a Python script that cleans up old EC2 Volume snapshots
- Write a Python script that restores EC2 Volumes

## Screenshots

![EC2 volumes](images/volumes.png)  
_Two 8 GiB gp3 EBS volumes in eu-central-1b. Only the volume tagged `Name: prod` is selected for backups._

![EBS snapshots](images/snapshots.png)  
_`volume-backups.py` runs on a schedule and calls `create_snapshot` for each `prod` volume. New snapshots start as Pending and move to Completed._

### Clean Up Old Snapshots

![Snapshot cleanup script output](images/snapshot%20cleanup%20python.png)  
_`cleanup-snapshots.py` sorts each `prod` volume's snapshots by start time and calls `delete_snapshot` on all but the two newest. Each deletion returns HTTP 200._

![Remaining snapshots after cleanup](images/snapshot%20clean%20up%20aws.png)  
_After the cleanup only the two most recent snapshots are left in the EC2 console._

### Restore Volume from Snapshot

![Restore script output](images/ec2%20available%20status.png)  
_`restore-volume.py` finds the instance's newest snapshot, calls `create_volume` from it, and polls the new volume's state until it changes from `creating` to `available`._

![Restored volume in the EC2 console](images/restore%20snapshot%20as%20volume.png)  
_The restored volume, tagged `Name: prod`, shows up in the EC2 console as Available in eu-central-1a, created from the snapshot._

<br>
