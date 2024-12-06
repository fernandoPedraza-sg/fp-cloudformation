
This repository contains several AWS CloudFormation templates that enable StratusGrid cloud engineers to perform cost optimization assessments and remediations. During the assessment project phase, only read permissions are needed. After the assessment and approval of a remediation plan, additional write permissions will be required by engineers.

# Files Description

## AWS account deployment.

The CloudFormation templates can be deployed to standalone AWS accounts, and these have the AWSAccountId as a unique parameter.

- awsacc-sg-read-only.json: this CloudFormation template creates an IAM role with read-only permissions for the assessment phase of cost optimization projects.

 - awsacc-sg-write-restricted.json: this CloudFormation template creates an IAM role with write permissions to specific AWS services for the assessment phase of cost optimization projects.

## AWS organization deployment.

The CloudFormation templates must be deployed to the management account of an AWS organization. These create resources in all AWS accounts that belong to a specific organizational unit (OU) or an organization.

- ou-sg-read-only.json: this CloudFormation template creates an IAM role with read-only permissions for the assessment phase of cost optimization projects.

- ou-sg-write-restricted.json: this CloudFormation template creates an IAM role with write permissions to specific AWS services for the assessment phase of cost optimization projects.

# AWS Cloudformation StackSet creation instructions:

- Navigate to the AWS Console and log in to your Management Account. Switch to the region where you want to deploy the StackSet.
- Go to the CloudFormation section of the AWS Console and select StackSets.
- Click Create StackSet.
![1](.images/Screenshot2024-12-05at4.39.56PM.png)
- Select Upload a template file, click Choose file, and select "ou-sg-read-only.json". Click Next
![2](.images/Screenshot2024-12-05at4.43.32PM.png)
- Enter the StackSet name, for instance, StratusGrid-IAM-ReadOnly. Click Next.
![3](.images/Screenshot2024-12-05at4.45.46PM.png)
- Scroll to the bottom of the page. Check to acknowledge that IAM role resources are being created, then click Submit.
![4](.images/Screenshot2024-12-05at4.46.13PM.png)
- Enter the AWS OU ID. The resource being created is an IAM role, and IAM is a global service; however, a region must be specified. Select the region where you are creating the StackSet, then click Next.

![5](.images/Screenshot2024-12-05at4.51.08PM.png)
- Scroll to the bottom of the page, then click Submit.

![6](.images/Screenshot2024-12-05at4.53.11PM.png)
- The StackSet will then deploy!

Repeat the CF stackset creation process for template "ou-sg-write-restricted.json"

![7](.images/Screenshot2024-12-05at5.02.07PM.png)

![8](.images/Screenshot2024-12-05at5.03.18PM.png)