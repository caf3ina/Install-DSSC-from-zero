# SmartCheck-0tohero
Smart Check is a container image scanner (Malware, Secrets, Vulnerabilities and dependencies) from Trend Micro.

# Setup the Enviroment
* Install AWS CLI - https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html
* HELM https://helm.sh/docs/intro/install/
* Install eksctl - https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html#install-eksctl-linux2

# EKS Cluster and Nodes (IAM)
We need two users one for EKS and another for Nodes with permissions bellow.

* IAM - Cluster - AmazonEKSClusterPolicy
* IAM - Nodes - AmazonEKSWorkerNodePolicy and AmazonEC2ContainerRegistryReadOnly

# Networking
Now, some components are important before start the cluster creation.

* VPC
* Subnet (Two different AZ and enable the Auto Assign IPv4)
* Internet Gateway
* One Security Group
* Nat Gateway

# AWS Configure and login Cluster
Set the credencials to acess the AWS console.

`$aws configure`
`$aws eks --region region update-kubeconfig --name cluster_name`
`$kubectl get svc`
