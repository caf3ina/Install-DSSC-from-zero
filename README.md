# SmartCheck-0tohero
Smart Check instalation from zero

# Setup the Enviroment
* Install AWS CLI - https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html
* HELM https://helm.sh/docs/intro/install/
* Install eksctk - https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html#install-eksctl-linux2

# EKS Cluster and Nodes (IAM)
We need two users one for EKS and another for Nodes with permissons above.

* IAM - Cluster - AmazonEKSClusterPolicy
* IAM - Nodes - AmazonEKSWorkerNodePolicy and AmazonEC2ContainerRegistryReadOnly

# Networking
Now, some components are important before start the cluster criation.

* VPC
* Subnet (Two different AZ and enable the Auto Assign IPv4)
* Internet Gateway
* One Security Group