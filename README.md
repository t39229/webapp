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
Open terraform folder with vscode.
change in terraform.ftvars acr_name to your uniq value.
Run terraform commands:
~ terraform init
~ terraform plan
~ terraform apply
Once the following resources are created:
Move the generated Kubeconfig file to ~/.kube/config
mv kubeconfig ~/.kube/config.
Run kubectl get no -A and verify 2 nodes are created.

Deploy web application.
![image](https://github.com/user-attachments/assets/3493f37d-1ab9-45e1-8f5f-51b57c2a3ed6)

Download web-app folder contains yaml files as follows:
Store front: Web application for customers to view products and place orders.
Product service: Shows product information.
Order service: Places orders.
Rabbit MQ: Message queue for an order queue.

open terminal and run command to deploy yaml files:
~ kubectl apply -f web-app
The deployment and services should be deployed under namespace "app"
Run kubectl get po -A -n app and verify all services under namespace app deployed succesfully.
Check for a public IP address for the store-front application. Monitor progress using the kubectl get service command with the --watch argument.
~ kubectl get service store-front --watch
Once the EXTERNAL-IP address changes from pending to an actual public IP address, use CTRL-C to stop the kubectl watch process.
Open a web browser to the external IP address of your service to see the Azure Store app in action.
Note: the following deploymnet set with replicas:2 as highly aviability solution
you can see it that 2 pods of each service running on different node by command:  kubectl get po -n app -o wide
