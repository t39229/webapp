Deploy web appliaction store in AKS using terraform
The following repository splited to 2 part:
1. Deploy AKS cluster using Terraform
2. Deploy web application

Deploy AKS cluster using Terraform
![image](https://github.com/user-attachments/assets/0cb6571f-6b6d-4a78-b9a3-50306a23e5e4)


Pre-requisites:
Terraform is installed on your machine.
Azure subscription
Kubectl is installed on your machine
Azure cli is installed
Login to Azure using credentials
Make sure you are login to Azure portal first.
az login
Choose your Microsoft credentials.
Git clone to your machine https://github.com/t39229/webapp.git 
Open terraform folder with vscode
change in terraform.ftvars acr_name to your uniq value.
Run terraform commands:
~ terraform init
~ terraform plan
~ terraform apply
Once the following resources are created:
Move the generated Kubeconfig file to ~/.kube/config
mv kubeconfig ~/.kube/config
Run kubectl get no -A and verify 2 nodes created.
