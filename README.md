I created this because there are lot of steps (I always forget) to configure K8S and install the DSSC. This how-to is one way to do this.

# Install-DSSC-from-zero
Smart Check is a container image scanner (Malware, Secrets, Vulnerabilities and dependencies) from Trend Micro.

# Setup the Enviroment
* Install AWS CLI - https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html
* HELM https://helm.sh/docs/intro/install/
* Install eksctl - https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html#install-eksctl-linux2

# EKS Cluster - Nodes - ECR Integration (IAM)
We need two users one for EKS and another for Nodes with permissions bellow.

* IAM Role - Cluster - AmazonEKSClusterPolicy
* IAM Role - Nodes - AmazonEKSWorkerNodePolicy, AmazonEC2ContainerRegistryReadOnly
* IAM User - DSSC and Registry AmazonEC2ContainerRegistryFullAccess

# Networking
Now, some components are important before start the cluster creation. 

* VPC
* Subnet (Two different AZ and enable the Auto Assign IPv4)
* Internet Gateway and attach in VPC
* One Security Group

# Access the AWS Console
* Go to Elastic Kubernetes Service and create the cluster (it takes some minutes)
* Add the Nodes

# AWS Configure and login Cluster
Set the credentials to access the AWS console.

* `$aws configure`
* `$aws eks --region region update-kubeconfig --name cluster_name`
* `$kubectl get svc`

# Now the easy part install Smart Check 
You can follow this link, the documentation is always updated https://github.com/deep-security/smartcheck-helm

# Let's create a Repository
* Go to Amazon Elastic Container Registry and create one
* Follow the steps to add a registry in DSSC https://deep-security.github.io/smartcheck-docs/admin_docs/admin.html#registry

* Now jut push the image to DSSC and wait :)
