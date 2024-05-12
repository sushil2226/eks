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