# eks
# steps to create EKS 

1. Create system level user to access aws account 
2. Overall eks setup :  
    Provision an EKS cluster --> Deploy worker nodes --> Connect to EKS --> Run/Deploy Kubernetes app

Step 1 
# Provision an EKS cluster 
1. Create IAM role, refer : https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/eks_cluster
2. Get VPC details
3. Create EKS cluster

Step 2
# Deploy worker node : https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/eks_node_group
1. Create IAM role
2. Create node groupe

Step 3
# Connect to EKS 
`aws eks --region <region code > update-kubeconfig --name <eks cluster name>`


.. 
# addons 
To store terraform statefile at s3 , use `backend`block
terraform {
  backend "s3" {
    bucket         = "my-terraform-state-bucket"  # Your S3 bucket name
    key            = "path/to/my/terraform.tfstate"
    region         = "us-west-2"                  # Bucket region
    encrypt        = true                         # Ensure this is enabled for security  -- optional
    dynamodb_table = "my-lock-table"              # DynamoDB table for state locking   -- optional
  }
}   


# Application deployment on EKS 

# Create po in eks 
k run nginx --image=nginx 

# expose pod port 
k port-forward pod/nginx 8080:80

# to check if nginx web server working , from laptop browser hit 
http://localhost:8080/

# To connect/go inside the pod 
k exec -it nginx -- /bin/bash

# Helm 



