# Infrastructure deployment by terraform for AWS Cloud.

## Getting started

## Prerequisites

Before you begin, ensure you have installed terraform (>=1.0.2), AWS SDK/CLI and other necessary tools.

- Install terraform using binary file and configure env path at local desktop by following below guide.
        https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli

- Install AWS CLI at local desktop
- Get Access key and secret key from IDP and pass the keys as an export/environment variables.



## How to provision resources

Step 1: Create a new branch from main/master.
Step 2: Make changes, Commit and push the code into git.
Step 3: Run terraform init, plan and apply from respective resource directory in newly created branch.
    ex: cd terraform/iac-deployments/projects/cdw/business-units/adas/aws/deployments/ec2-bastion

    - terraform init

       terraform init --backend-config =<<path of the config file where it stores the GCS bucket name as config to store remote state files.>>
       ex: terraform init --backend-config =../../terraform_config/prod/ap-south-1.config

    - terraform plan

       terraform plan -var-file=<<path of the terraform.tfvars file where we store the variable input values.>>
       ex: terraform plan -var-file=../../terraform_config/prod/ec2-bastion/ap-south-1.tfvars

    - terraform apply

       terraform apply -var-file=<<path of the terraform.tfvars file where we store the variable input values.>>
       ex: terraform apply -var-file=../../terraform_config/prod/ec2-bastion/ap-south-1.tfvars

    

## Note:

- If we provisioned the resources from local desktop, needs to setup AWS cli and needs to pass access/secret keys as environment variables. refer below doc to initialize the gcloud CLI.
- In filename.config needs to update the bucket name based on the project/environment/region.
- In deployments each resource/folder will have remote_state.tf, where we store the prefix(name of the S3 Object) to store the state file. If needs to create new resource (ex: new S3 with different name), please change the prefix name too. otherwise it will overwrite existing/old resources based on the prefix (state file)
- please don't push unwanted files/folders like modules, .terraform, .lock.hcl files
