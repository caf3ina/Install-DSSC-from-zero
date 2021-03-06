I created this because there are many steps (I always forget :D) to set up an infrastructure with K8S on AWS. This manual is one way to do this.

# About the Tool
Smart Check is a container image scanner (Malware, Secrets, Vulnerabilities and dependencies) from Trend Micro

* More information in https://www.trendmicro.com/en_us/business/products/hybrid-cloud/smart-check-image-scanning.html
* API https://deep-security.github.io/smartcheck-docs/api/index.html

# Setup the Enviroment
* Install AWS CLI - https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html
* HELM https://helm.sh/docs/intro/install/
* Install eksctl - https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html#install-eksctl-linux2

We need two roles and one user

* IAM Role (EKS) - Cluster - AmazonEKSClusterPolicy, AmazonEKSServicePolicy, AmazonEKSWorkerNodePolicy
* IAM Role (EC2) - Nodes - AmazonEKSWorkerNodePolicy, AmazonEC2ContainerRegistryReadOnly, AmazonEKS_CNI_Policy, AmazonEKSServicePolicy and ElasticLoadBalancingFullAccess
* IAM User for DSSC integration - AmazonEC2ContainerRegistryFullAccess and AmazonECS_FullAccess

Now, some components are important before start the cluster creation. 

* VPC - https://aws.amazon.com/pt/blogs/containers/de-mystifying-cluster-networking-for-amazon-eks-worker-nodes/

`Public only subnets` https://amazon-eks.s3.us-west-2.amazonaws.com/cloudformation/2020-03-23/amazon-eks-vpc-sample.yaml


# Access the AWS Console
* Go to Elastic Kubernetes Service and create the cluster (it takes some minutes)
* Add the Nodes

# AWS Configure and login Cluster
Set the credentials to access the AWS console.

* `$aws configure`
* `$aws eks --region region update-kubeconfig --name cluster_name`
* `$kubectl get svc`

# Now the easy part install Smart Check 
* You can follow this link, the documentation is always updated https://github.com/deep-security/smartcheck-helm
* Problems with yaml? http://www.yamllint.com/

# Let's create a Repository
* Go to Amazon Elastic Container Registry
* Follow the steps to add a registry in DSSC https://deep-security.github.io/smartcheck-docs/admin_docs/admin.html#registry

* Now just push the image to DSSC and wait :)

![Smart Check Dashboard.png](https://github.com/caf3ina/Vulnerability-and-Malware-Assessment-for-Containers/blob/https/github.com/caf3ina/BIO/Smart%20Check%20Dashboard.png)

