# sample-ecs-deployment
Using AWS CodeBuild, CodeDeploy and CodePipeline

## Create IAM roles
### Code pipeline service role
 Execute the following using aws cli
```bash
aws iam create-role --role-name CodePipelineRole --assume-role-policy-document file://iam/codepipeline-trust-policy.json --profile devopsengineer

aws iam put-role-policy --role-name CodePipelineRole --policy-name CodePipelinePolicy --policy-document file://iam/codepipeline-policy.json --profile devopsengineer
```
### Code build service role
 Execute the following using aws cli
```bash
aws iam create-role --role-name CodeBuildRole --assume-role-policy-document file://iam/codebuild-trust-policy.json --profile devopsengineer

aws iam put-role-policy --role-name CodeBuildRole --policy-name CodeBuildPolicy --policy-document file://iam/codebuild-policy.json --profile devopsengineer
```
### Cloudformation execution role
```bash
aws iam create-role --role-name CloudFormationExecutionRole --assume-role-policy-document file://iam/cloudformation-trust-policy.json --profile devopsengineer
```
Attach the AWS Managed Policy arn:aws:iam::aws:policy/AdministratorAccess to the above role
### ECS task execution role
```bash
aws iam create-role --role-name EcsTaskExecutionRole --assume-role-policy-document file://iam/ecs-trust-policy.json --profile devopsengineer
```
Attach the AWS Managed Policy to the above role, arn:aws:iam::aws:policy/service-role/AmazonECSTaskExecutionRolePolicy