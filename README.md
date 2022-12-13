# ECS_Deployment
CI/CD to deploy Public Docker image to AWS using ECS

We are using ECS service to deploy the image on AWS 
ECS acts as an Entrypoint service that allows us to run Docker Containers on AWS infrastructure along with other AWS services to complete things 

By Configuring ECS with the help of template file the task can be automated instead of using the Web UI and finally using the ECS Fargate launch type for deployment

Steps :

cloud formation->
aws cloudformation create-stack
--stack-name example-deployment ESTaskExecutionRolePolicy
ContainerSecurityGroup:
--template-body file:///ecs.yml
--capabilities CAPABILITY_NAMED_IAM
--parameters 'ParameterKey=SubnetID,ParameterValue=subnet-1881f750'

Task definition->
aws cloudformation update-stack
--stack-name example-deployment
--template-body file://./ecs.yml
--capabilities CAPABILITY_NAMED_IAM
--parameters 'ParameterKey=SubnetID,ParameterValue=subnet-1881f750'


