# Supported Resources<a name="supported-resources"></a>

You can use the AWS Management Console or the AWS CLI to add tags to many AWS resources\. This topic describes resources that you can query and group into resource groups by using AWS Resource Groups, and resources that you can tag by using Tag Editor\.

**Topics**
+ [Supported Resources for AWS Resource Groups](#supported-resources-console)
+ [Supported Resources for Tag Editor Tagging](#supported-resources-tagging-console)

## Supported Resources for AWS Resource Groups<a name="supported-resources-console"></a>

Use the AWS Resource Groups service to create groups for the following AWS resources\. The supported resources vary slightly depending on whether you are creating a tag\-based or an AWS CloudFormation stack\-based group\. Resources for global services \(such as Amazon CloudFront and Route 53\) appear only in the US East \(N\. Virginia\) Region \(us\-east\-1\)\.

**Important**  
A resource group based on a query for **All supported resource types** can add members automatically over time, as new resources are supported by Resource Groups\. When you run automations or other bulk tasks on an existing resource group based on **All supported resource types**, be aware that the actions might be run on many more resources than were in the group when you first created it\. This might also mean that automations or tasks that you created for other resources are applied to unintended resources, or resources on which the tasks cannot be completed\.  

![\[Query based on All supported resource types.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-allsupported-resources.png)

**Topics**
+ [Supported Resources for Tag\-based Groups](#supported-resources-console-tagbased)
+ [Supported Resources for AWS CloudFormation Stack\-based Groups](#supported-resources-console-stackbased)

### Supported Resources for Tag\-based Groups<a name="supported-resources-console-tagbased"></a>


| **Service** | **Resources** | 
| --- | --- | 
|  Amazon API Gateway  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon AppStream  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Certificate Manager  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS CloudFormation  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon CloudFront  |  \(Supported only in the US East \(N\. Virginia\) Region, `us-east-1`\.\) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS CloudTrail  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon CloudWatch  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon CloudWatch Events  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon CloudWatch Logs  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS CodeBuild  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS CodeCommit  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS CodePipeline  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Cognito  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Config  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Data Pipeline  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Database Migration Service  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon DynamoDB  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Elastic Beanstalk  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Elastic Compute Cloud \(Amazon EC2\)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Elastic Container Registry  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Elastic Container Service  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon ElastiCache  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Elastic File System  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Elastic Load Balancing  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon EMR  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Elasticsearch Service  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon FSx  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon S3 Glacier  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Glue  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Inspector  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS IoT  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS IoT Analytics  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS IoT Events  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Key Management Service  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Kinesis  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Kinesis Data Analytics  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Kinesis Data Firehose  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Lambda  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Managed Streaming for Apache Kafka  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon MQ  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS OpsWorks  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
| AWS Organizations |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Quantum Ledger Database \(Amazon QLDB\)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Redshift  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Relational Database Service \(Amazon RDS\)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Resource Access Manager  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Resource Groups  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS RoboMaker  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Route 53  |  \(Supported only in the US East \(N\. Virginia\) Region, `us-east-1`\.\) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Route 53 Resolver  |  \(Supported only in the US East \(N\. Virginia\) Region, `us-east-1`\.\) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon SageMaker  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
| AWS Secrets Manager |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Service Catalog  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Simple Notification Service  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Simple Queue Service  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Simple Storage Service \(Amazon S3\)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Step Functions  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Storage Gateway  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Systems Manager  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon WorkSpaces  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 

### Supported Resources for AWS CloudFormation Stack\-based Groups<a name="supported-resources-console-stackbased"></a>


| **Service** | **Resources** | 
| --- | --- | 
|  Amazon API Gateway  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS AppSync  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Certificate Manager  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
| AWS CloudFormation |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon CloudFront  |  \(Supported only in the US East \(N\. Virginia\) Region, `us-east-1`\.\) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS CloudTrail  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon CloudWatch  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon CloudWatch Events  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon CloudWatch Logs  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS CodeDeploy  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS CodePipeline   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Cognito  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Data Pipeline  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Database Migration Service  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon DynamoDB  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Elastic Compute Cloud \(Amazon EC2\)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Elastic File System  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Elastic Load Balancing  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon ElastiCache  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Elasticsearch Service  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon EMR  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Glue  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Identity and Access Management \(IAM\)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS IoT   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS IoT Events   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Inspector  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Key Management Service  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Kinesis  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Lambda  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS OpsWorks  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Quantum Ledger Database \(Amazon QLDB\)   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Redshift  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Relational Database Service \(Amazon RDS\)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Route 53  |  \(Supported only in the US East \(N\. Virginia\) Region, `us-east-1`\.\) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon SageMaker  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Secrets Manager  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Service Catalog  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Simple Notification Service  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Simple Queue Service  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Simple Storage Service \(Amazon S3\)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Step Functions  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Systems Manager  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon WorkSpaces  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 

## Supported Resources for Tag Editor Tagging<a name="supported-resources-tagging-console"></a>

You can use Tag Editor in the AWS Management Console to tag the following AWS resources\. For more information, see [Tag Editor](tag-editor.md)\.


| **Service** | **Resources** | 
| --- | --- | 
|  AWS CloudFormation  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon CloudFront   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon CloudWatch  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon CloudWatch Events  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS CodeBuild   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS CodePipeline   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Cognito   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Config   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Data Pipeline  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon DynamoDB  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Elastic Beanstalk  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Elastic Compute Cloud \(Amazon EC2\)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Elastic Load Balancing  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon ElastiCache  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Elasticsearch Service   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon EMR  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon FSx   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  S3 Glacier  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Glue   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS IoT Analytics   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS IoT Events   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Key Management Service   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Kinesis  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Kinesis Data Analytics   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Lambda  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Managed Streaming for Apache Kafka   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon MQ   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Organizations   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Quantum Ledger Database \(Amazon QLDB\)   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Redshift  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Relational Database Service \(Amazon RDS\)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Resource Access Manager  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Resource Groups  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS RoboMaker   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Route 53  |  \(Supported only in the US East \(N\. Virginia\) Region, `us-east-1`\.\) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon SageMaker   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  Amazon Simple Storage Service \(Amazon S3\)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Systems Manager   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Step Functions   |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 
|  AWS Storage Gateway  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/supported-resources.html)  | 