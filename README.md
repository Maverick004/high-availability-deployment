### Deploy a High Availability web app using AWS CloudFormation

In this repository;
* naruto_network.yml
Template containing all the network resources to be deployed. Deploy this first.

* sasuke_server.yml
Template containing all the app resources to be deployed. Deploy this after deploying the network resources.

* networking-parameters.json
Parameters that you can tweak to customise network infrastructure

* server-params
Parameters that you can tweak to customise server infrastructure

* create.bat
Batch script to create infrastructure

* update.bat
Batch script to update infrastructure

* EnvironmentName: The EnvironmentName you want to use for the deployment
* VpcCIDR: The CIDR of your VPC
* PublicSubnet1CIDR/PublicSubnet2CIDR/PrivateSubnet1CIDR/PrivateSubnet2CIDR: The - CIDR of your public and private subnets
* infrastructure_diagram.png
* 
The infrastructure Diagram
![Deployment  Architecture](https://user-images.githubusercontent.com/108627847/181870217-e165c290-7c72-4f0c-ab38-addc8a76d92a.jpeg)

### Prerequisites
A user account with programmatic access to AWS via CLI

To run
Create network stack using the following command:
`aws cloudformation create-stack --stack-name %1 --template-body file://%2  --parameters file://%3 --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-west-2`

Wait a few minutes for the stack creation to complete. Check the status with aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE

Create the server stack:
`aws cloudformation create-stack --stack-name %1 --template-body file://%2  --parameters file://%3 --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-west-2`

Output
The IP address of the load balancer (among other results)
In this case `http://sasuk-webap-zzi1ms87fw7f-1637582047.us-west-2.elb.amazonaws.com/`
