# Supported Resources<a name="supported-resources"></a>

You can use the AWS Management Console or the AWS CLI to add tags to many AWS resources\. This topic describes resources that you can query and group into resource groups by using AWS Resource Groups, and resources that you can tag by using Tag Editor\.

**Important**  
A resource group based on a query for **All supported resource types** can add members automatically over time, as new resources are supported by Resource Groups\. When you run automations or other bulk tasks on an existing resource group based on **All supported resource types**, be aware that the actions might be run on many more resources than were in the group when you first created it\. This might also mean that automations or tasks that you created for other resources are applied to unintended resources, or resources on which the tasks cannot be completed\.  

![\[Query based on All supported resource types.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-allsupported-resources.png)

The following tables list which resources are supported for tag\-based groups, tagging in Tag Editor, and for AWS CloudFormation stack\-based groups\. 

## Amazon API Gateway<a name="api-gateway"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::ApiGateway::Account | No | No | Yes | 
| AWS::ApiGateway::ApiKey | No | No | Yes | 
| AWS::ApiGateway::DomainName | No | No | Yes | 
| AWS::ApiGateway::RestApi | No | Yes | Yes | 
| AWS::ApiGateway::Stage | No | Yes | No | 
| AWS::ApiGateway::UsagePlan | No | No | Yes | 

## Amazon AppStream<a name="appstream"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::AppStream::Fleet | No | Yes | No | 
| AWS::AppStream::ImageBuilder | No | Yes | No | 
| AWS::AppStream::Stack | No | Yes | No | 

## AWS AppSync<a name="appsync"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::AppSync::DataSource | No | No | Yes | 
| AWS::AppSync::GraphQLApi | No | No | Yes | 

## AWS Certificate Manager<a name="certificate-manager"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::CertificateManager::Certificate | No | Yes | Yes | 

## AWS CloudFormation<a name="cloudformation"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::CloudFormation::Stack | Yes | Yes | Yes | 

## Amazon CloudFront<a name="cloudfront"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::CloudFront::Distribution | Yes | Yes¹ | Yes¹ | 
| AWS::CloudFront::StreamingDistribution | Yes | Yes¹ | Yes¹ | 

¹ This is a resource for a global service that is hosted in the **US East \(N\. Virginia\)** Region\. Because Resource Groups are maintained separately for each region, you must switch your AWS console to the Region that contains the resources you want to include in the group\. To create a resource group that contains a global resource, you must configure your AWS Console to **US East \(N\. Virginia\) us\-east\-1** using the Region selector in the upper\-right corner of the AWS console\.

## AWS CloudTrail<a name="cloudtrail"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::CloudTrail::Trail | No | Yes | Yes | 

## Amazon CloudWatch<a name="cloudwatch"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::CloudWatch::Alarm | Yes | Yes | Yes | 
| AWS::CloudWatch::Dashboard | No | No | Yes | 

## Amazon CloudWatch Events<a name="cloudwatchevents"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Events::Rule | Yes | Yes | Yes | 

## Amazon CloudWatch Logs<a name="cloudwatchlogs"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Logs::LogGroup | No | Yes | Yes | 

## AWS CodeBuild<a name="codebuild"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::CodeBuild::Project | Yes | Yes | No | 

## AWS CodeCommit<a name="codecommit"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::CodeCommit::Repository | No | Yes | No | 

## AWS CodeDeploy<a name="codedeploy"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::CodeDeploy::Application | No | No | Yes | 
| AWS::CodeDeploy::DeploymentConfig | No | No | Yes | 

## AWS CodePipeline<a name="codepipeline"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::CodePipeline::Pipeline | Yes | Yes | Yes | 
| AWS::CodePipeline::Webhook | Yes | Yes | Yes | 

## Amazon Cognito<a name="cognito"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS:Cognito::IdentityPool | Yes | Yes | Yes | 
| AWS::Cognito::UserPool | Yes | Yes | Yes | 

## AWS Config<a name="config"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Config::ConfigRule | Yes | Yes | No | 

## AWS Data Exchange<a name="dataexchange"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::DataExchange::DataSet | Yes | Yes | No | 
| AWS::DataExchange::Revision | No | Yes | No | 

## AWS Data Pipeline<a name="datapipeline"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::DataPipeline::Pipeline | Yes | Yes | Yes | 

## AWS Database Migration Service<a name="databasemigrationservice"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::DMS::Certificate | No | Yes | No | 
| AWS::DMS::Endpoint | No | Yes | Yes | 
| AWS::DMS::EventSubscription | No | Yes | No | 
| AWS::DMS::ReplicationInstance | No | Yes | Yes | 
| AWS::DMS::ReplicationSubnetGroup | No | Yes | No | 
| AWS::DMS::ReplicationTask | No | Yes | No | 

## Amazon DynamoDB<a name="dynamodb"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::DynamoDB::Table | Yes | Yes | Yes | 

## AWS Elastic Beanstalk<a name="elasticbeanstalk"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| >AWS::ElasticBeanstalk::Application | Yes | Yes | No | 
| AWS::ElasticBeanstalk::ApplicationVersion | No | Yes | No | 
| AWS::ElasticBeanstalk::ConfigurationTemplate | No | Yes | No | 
| AWS::ElasticBeanstalk::Environment | No | Yes | No | 

## Amazon Elastic Compute Cloud \(Amazon EC2\)<a name="ec2"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::EC2::CapacityReservation | No | Yes | No | 
| AWS::EC2::CustomerGateway | Yes | Yes | Yes | 
| AWS::EC2::DHCPOptions | Yes | Yes | Yes | 
| AWS::EC2::EIP | Yes | Yes | No | 
| AWS::EC2::Host | No | Yes | No | 
| AWS::EC2::Image | Yes | Yes | No | 
| AWS::EC2::Instance | Yes | Yes | Yes | 
| AWS::EC2::InternetGateway | Yes | Yes | Yes | 
| AWS::EC2::LaunchTemplate | No | Yes | Yes | 
| AWS::EC2::NatGateway | No | Yes | Yes | 
| AWS::EC2::NetworkAcl | Yes | Yes | Yes | 
| AWS::EC2::NetworkInterface | Yes | Yes | Yes | 
| AWS::EC2::ReservedInstance | Yes | Yes | No | 
| AWS::EC2::RouteTable | Yes | Yes | Yes | 
| AWS::EC2::SecurityGroup | Yes | Yes | Yes | 
| AWS::EC2::Snapshot | Yes | Yes | No | 
| AWS::EC2::SpotInstanceRequest | Yes | Yes | No | 
| AWS::EC2::Subnet | Yes | Yes | Yes | 
| AWS::EC2::TransitGateway | No | Yes | No | 
| AWS::EC2::TransitGatewayRouteTable | No | Yes | No | 
| AWS::EC2::Volume | Yes | Yes | Yes | 
| AWS::EC2::VPC | Yes | Yes | Yes | 
| AWS::EC2::VPCPeeringConnection | No | Yes | Yes | 
| AWS::EC2::VPNConnection | Yes | Yes | Yes | 
| AWS::EC2::VPNGateway | Yes | Yes | Yes | 

## Amazon Elastic Container Registry<a name="ecr"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::ECR::Repository | No | Yes | No | 

## Amazon Elastic Container Service<a name="elasticcontainerservice"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::ECS::Cluster | No | Yes | No | 
| AWS::ECS::ContainerInstance | No | Yes | No | 
| AWS::ECS::Service | No | Yes | No | 
| AWS::ECS::Task | No | Yes | No | 
| AWS::ECS::TaskDefinition | No | Yes | No | 

## Amazon Elastic File System<a name="elasticfilesystem"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::EFS::FileSystem | No | Yes | Yes | 

## Elastic Load Balancing<a name="elasticloadbalancing"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::ElasticLoadBalancing::LoadBalancer | Yes | Yes | Yes | 
| AWS::ElasticLoadBalancingV2::LoadBalancer | Yes | Yes | Yes | 
| AWS::ElasticLoadBalancingV2::TargetGroup | Yes | Yes | Yes | 

## Amazon ElastiCache<a name="elasticache"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::ElastiCache::CacheCluster | Yes | Yes | Yes | 
| AWS::ElastiCache::Snapshot | Yes | Yes | No | 

## Amazon Elasticsearch Service<a name="elasticsearch"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Elasticsearch::Domain | Yes | Yes | Yes | 

## Amazon EMR<a name="emr"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::EMR::Cluster | Yes | Yes | Yes | 

## Amazon FSx<a name="fsx"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::FSx::FileSystem | Yes | Yes | No | 

## AWS Glue<a name="glue"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Glue::Crawler | Yes | Yes | No | 
| AWS::Glue::Database | No | No | Yes | 
| AWS::Glue::Job | Yes | Yes | No | 
| AWS::Glue::Trigger | Yes | Yes | No | 

## AWS Identity and Access Management<a name="iam"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::IAM::Role | No | No | Yes | 

## Amazon Inspector<a name="inspector"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Inspector::AssessmentTemplate | No | Yes | Yes | 

## AWS IoT<a name="iot"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::IoT::TopicRule | No | Yes | Yes | 

## AWS IoT Analytics<a name="iot-analytics"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::IoTAnalytics::Channel | No | Yes | No | 
| AWS::IoTAnalytics::Dataset | Yes | Yes | No | 
| AWS::IoTAnalytics::Datastore | No | Yes | No | 
| AWS::IoTAnalytics::Pipeline | No | Yes | No | 

## AWS IoT Events<a name="iot-events"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::IoTEvents::DetectorModel | Yes | Yes | Yes | 
| AWS::IoTEvents::Input | Yes | Yes | Yes | 

## AWS IoT Greengrass<a name="iot-greengrass"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Greengrass::ConnectorDefinition | Yes | Yes | No | 
| AWS::Greengrass::CoreDefinition | Yes | Yes | No | 
| AWS::Greengrass::DeviceDefinition | Yes | Yes | No | 
| AWS::Greengrass::FunctionDefinition | Yes | Yes | No | 
| AWS::Greengrass::Group | Yes | Yes | No | 
| AWS::Greengrass::LoggerDefinition | Yes | Yes | No | 
| AWS::Greengrass::ResourceDefinition | Yes | Yes | No | 
| AWS::Greengrass::SubscriptionDefinition | Yes | Yes | No | 

## AWS Key Management Service<a name="kms"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::KMS::Alias | No | No | Yes | 
| AWS::KMS::Key | Yes | Yes | Yes | 

## Amazon Kinesis<a name="kinesis"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Kinesis::Stream | Yes | Yes | Yes | 

## Amazon Kinesis Data Analytics<a name="kinesis-data-analytics"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::KinesisAnalytics::Application | Yes | Yes | No | 

## Amazon Kinesis Data Firehose<a name="kinesis-firehose"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::KinesisFirehose::DeliveryStream | No | Yes | No | 

## AWS Lambda<a name="lambda"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Lambda::Alias | No | No | Yes | 
| AWS::Lambda::EventSourceMapping | No | No | Yes | 
| AWS::Lambda::Function | Yes | Yes | Yes | 
| AWS::Lambda::LayerVersion | No | No | Yes | 
| AWS::Lambda::Version | No | No | Yes | 

## Amazon Managed Streaming for Apache Kafka<a name="kafka"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Kafka::Cluster | Yes | Yes | No | 

## Amazon MQ<a name="mq"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::AmazonMQ::Broker | Yes | Yes | No | 
| AWS::AmazonMQ::Configuration | Yes | Yes | No | 

## AWS OpsWorks<a name="opsworks"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::OpsWorks::Instance | No | Yes | Yes | 
| AWS::OpsWorks::Layer | No | Yes | Yes | 
| AWS::OpsWorks::Stack | No | Yes | Yes | 

## AWS Organizations<a name="organizations"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Organizations::Account | Yes | Yes | No | 

## Amazon Quantum Ledger Database \(Amazon QLDB\)<a name="qldb"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::QLDB::Ledger | Yes | Yes | Yes | 

## Amazon Redshift<a name="redshift"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Redshift::Cluster | Yes | Yes | Yes | 
| AWS::Redshift::ClusterParameterGroup | Yes | Yes | Yes | 
| AWS::Redshift::ClusterSecurityGroup | No | Yes | Yes | 
| AWS::Redshift::ClusterSubnetGroup | Yes | Yes | Yes | 
| AWS::Redshift::HSMClientCertificate | Yes | Yes | No | 

## Amazon Relational Database Service \(Amazon RDS\)<a name="rds"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::RDS::DBCluster | No | Yes | Yes | 
| AWS::RDS::DBClusterParameterGroup | No | Yes | Yes | 
| AWS::RDS::DBClusterSnapshot | No | Yes | No | 
| AWS::RDS::DBInstance | Yes | Yes | Yes | 
| AWS::RDS::DBParameterGroup | Yes | Yes | Yes | 
| AWS::RDS::DBSecurityGroup | Yes | Yes | Yes | 
| AWS::RDS::DBSnapshot | Yes | Yes | No | 
| AWS::RDS::DBSubnetGroup | Yes | Yes | Yes | 
| AWS::RDS::EventSubscription | Yes | Yes | No | 
| AWS::RDS::OptionGroup | Yes | Yes | No | 
| AWS::RDS::ReservedDBInstance | Yes | Yes | No | 

## AWS Resource Access Manager<a name="ram"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::RAM::ResourceShare | Yes | Yes | No | 

## AWS Resource Groups<a name="resource-groups"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::ResourceGroups::Group | Yes | Yes¹ | No | 

¹ Lets you create a *nested* resource group, or a resource group that contains other resource groups\.

## AWS Robomaker<a name="robomaker"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::RoboMaker::DeploymentJob | Yes | Yes | No | 
| AWS::RoboMaker::Fleet | Yes | Yes | No | 
| AWS::RoboMaker::Robot | Yes | Yes | No | 
| AWS::RoboMaker::RobotApplication | Yes | Yes | No | 
| AWS::RoboMaker::SimulationApplication | Yes | Yes | No | 
| AWS::RoboMaker::SimulationJob | Yes | Yes | No | 

## Amazon Route 53<a name="route53"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Route53::Domain | Yes¹ | Yes² | No | 
| AWS::Route53::HealthCheck | Yes¹ | Yes² | Yes² | 
| AWS::Route53::HostedZone | Yes¹ | Yes² | Yes² | 

¹ This is a resource for a global service that is hosted in the **US East \(N\. Virginia\)** Region\. To use Tag Editor to create or modify tags for this resource type, you must include `us-east-1` from the **Select regions** list under **Find resources to tag** in the Tag Editor console\.

² This is a resource for a global service that is hosted in the **US East \(N\. Virginia\)** Region\. Because Resource Groups are maintained separately for each region, you must switch your AWS console to the Region that contains the resources you want to include in the group\. To create a resource group that contains a global resource, you must configure your AWS Console to **US East \(N\. Virginia\) us\-east\-1** using the Region selector in the upper\-right corner of the AWS console\.

## Amazon Route 53 Resolver<a name="route53-resolver"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Route53Resolver::ResolverEndpoint | No | Yes¹ | No | 
| AWS::Route53Resolver::ResolverRule | No | Yes¹ | No | 

¹ This is a resource for a global service that is hosted in the **US East \(N\. Virginia\)** Region\. Because Resource Groups are maintained separately for each region, you must switch your AWS console to the Region that contains the resources you want to include in the group\. To create a resource group that contains a global resource, you must configure your AWS Console to **US East \(N\. Virginia\) us\-east\-1** using the Region selector in the upper\-right corner of the AWS console\.

## Amazon SageMaker<a name="sagemaker"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::SageMaker::Endpoint | No | Yes | Yes | 
| AWS::SageMaker::EndpointConfig | No | Yes | Yes | 
| AWS::SageMaker::HyperParameterTuningJob | No | Yes | No | 
| AWS::SageMaker::LabelingJob | No | Yes | No | 
| AWS::SageMaker::Model | No | Yes | Yes | 
| AWS::SageMaker::NotebookInstance | Yes | Yes | Yes | 
| AWS::SageMaker::TrainingJob | No | Yes | No | 
| AWS::SageMaker::TransformJob | No | Yes | No | 
| AWS::SageMaker::Workteam | No | Yes | No | 

## AWS Secrets Manager<a name="secrets-manager"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::SecretsManager::Secret | No | Yes | Yes | 

## AWS Service Catalog<a name="service-catalog"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::ServiceCatalog::CloudFormationProduct | No | Yes | Yes | 
| AWS::ServiceCatalog::Portfolio | No | Yes | Yes | 

## Amazon Simple Notification Service<a name="sns"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::SNS::Topic | No | Yes | Yes | 

## Amazon Simple Queue Service<a name="sqs"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::SQS::Queue | No | Yes | Yes | 

## Amazon Simple Storage Service \(Amazon S3\)<a name="s3"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::S3::Bucket | Yes | Yes | Yes | 

## Amazon S3 Glacier<a name="s3-glacier"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::Glacier::Vault | Yes | Yes | No | 

## AWS Step Functions<a name="step-functions"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::StepFunctions::Activity | Yes | Yes | Yes | 
| AWS::StepFunctions::StateMachine | Yes | Yes | Yes | 

## AWS Storage Gateway<a name="storage-gateway"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::StorageGateway::Gateway | Yes | Yes | No | 
| AWS::StorageGateway::Volume | No | Yes | No | 

## AWS Systems Manager<a name="systems-manager"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::SSM::Document | No | Yes | Yes | 
| AWS::SSM::MaintenanceWindow | No | Yes | No | 
| AWS::SSM::ManagedInstance | No | Yes | No | 
| AWS::SSM::Parameter | Yes | Yes | Yes | 
| AWS::SSM::PatchBaseline | No | Yes | Yes | 

## Amazon WorkSpaces<a name="workspaces"></a>


| **Resources** | **Tag Editor Tagging** | **Tag\-based Groups** | **AWS CloudFormation Stack\-based Groups** | 
| --- | --- | --- | --- | 
| AWS::WorkSpaces::Workspace | No | Yes | Yes | 