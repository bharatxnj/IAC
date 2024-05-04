**Context**


![image](https://github.com/bharatxnj/IAC/assets/46646250/158d905e-424a-4008-ad4c-e4149924b3d5)



**Structure**

![image](https://github.com/bharatxnj/IAC/assets/46646250/32329fd8-07df-41c6-b82e-78fc1fb2515b)


**#Prerequisites
**
Install Git, AWS CLI Version 2, Terraform (v 0.13.2), Terragrunt (v 0.23.40) and few other necessary packages (curl, vim, and unzip)


#! /bin/bash
echo "###################################"
echo "Installing curl, git, vim and unzip"
echo "###################################"
apt-get update
apt-get install curl git vim unzip awscli -y
echo "############################################"
echo "Installing AWS CLI, Terraform and Terragrunt"
echo "############################################"
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
./aws/install
curl -L -o terraform.zip https://releases.hashicorp.com/terraform/0.13.6/terraform_0.13.6_linux_386.zip && unzip -o terraform.zip -d /usr/local/bin/
curl -L -o /usr/local/bin/terragrunt https://github.com/gruntwork-io/terragrunt/releases/download/v0.28.12/terragrunt_linux_386 && chmod u+x /usr/local/bin/terragrunt


**Run the below commands to confirm the installation once the above script completes.
**
git --version
aws --version
terraform -v
terragrunt -v

**To execute Terraform modules
**
git clone git@repo

=========================================END======================================================================================

## Note:

- If we provisioned the resources from local desktop, needs to setup AWS cli and needs to pass access/secret keys as environment variables. refer below doc to initialize the gcloud CLI.
- In filename.config needs to update the bucket name based on the project/environment/region.
- In deployments each resource/folder will have remote_state.tf, where we store the prefix(name of the S3 Object) to store the state file. If needs to create new resource (ex: new S3 with different name), please change the prefix name too. otherwise it will overwrite existing/old resources based on the prefix (state file)
- please don't push unwanted files/folders like modules, .terraform, .lock.hcl files
